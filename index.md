<style> 
h1 {text-align:center} 
</style> 

<strong> <h1> 欢迎来到青岛发动机工厂</h1> </strong> 


 <h2 id = "缸体线"> 缸体</h2>
<table border="0"> 
 
  <tr>
    <td width="75%">
      <h2>一期</h2>
      <p><b>缸体线</b></p>
         <h2>二期</h2>
      <p><b>缸体线</b></p> 
     
     
<!--      锚点链接 -->
     
 <a href = "#缸盖线" >  缸盖线  </a>    
  <a href = "#曲轴线"> 曲轴线 </a>
  <a href = "#缸体线"> 缸体线 </a>
    <a href = "#装配线"> 装配线 </a>
  各线查询
  
    <a href = "#装配线查询" > 装配线查询 </a>
    <a href = "#缸体线查询" > 缸体线查询 </a>
    <a href = "#曲轴线查询" > 曲轴线查询 </a>
    <a href = "#缸盖线查询" > 缸盖线查询 </a>
     

<a href = "http//www.baidu.com" target = "blank">查询地址</a>  <br>
<img src = "https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=1634963068,1747469511&fm=26&gp=0.jpg"/><br>



 <h2 id = "缸盖线"> 缸盖</h2>  <br/>
 
 
<table border="0">
  <tr>
    <td width="75%">
      <h2>一期</h2>
      <p><b>缸盖线</b></p>
         <h2>二期</h2>
      <p><b>缸盖线</b></p> 
   

<a href = "http//www.baidu.com" target = "blank">查询地址</a> <br>
<img src = "https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=3040044467,2582481343&fm=26&gp=0.jpg"/><br>


 <h2 id = "曲轴线"> 曲轴</h2>

<table border="0">
  <tr>
    <td width="75%">
      <h2>一期</h2>
      <p><b>曲轴线</b></p>
         <h2>二期</h2>
      <p><b>曲轴线</b></p> 


  <a   href = "http//www.baidu.com" target = "blank"   >查询地址</a> <br>
   <a id  = "装配线查询" > 装配线查询 </a> <br>

<img src = "https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1593491233148&di=f77a8fb541bbc4ae3020ea78c77b43b6&imgtype=0&src=http%3A%2F%2Fpics7.baidu.com%2Ffeed%2Fd62a6059252dd42a0b3bf20ef60b2fb1c9eab81e.jpeg%3Ftoken%3D34d566f263238cc8e95aa0a7dc712c8d%26s%3DD5E6B94475138BC80C7DA913010050C3"/><br>

 <h2 id = "装配线"> 装配</h2>

<table border="0">
  <tr>
    <td width="75%">
      <h2>一期</h2>
      <p><b>装配线</b></p>
         <h2>二期</h2>
      <p><b>装配线</b></p> 

<a href = "http//www.baidu.com" target = "blank">查询地址</a> <br>

<img src = "https://ss0.bdstatic.com/70cFuHSh_Q1YnxGkpoWK1HF6hhy/it/u=2038204091,2195930273&fm=26&gp=0.jpg"/><br>

//



# This workflow will build and push a new container image to Amazon ECR,
# and then will deploy a new task definition to Amazon ECS, when a release is created
#
# To use this workflow, you will need to complete the following set-up steps:
#
# 1. Create an ECR repository to store your images.
#    For example: `aws ecr create-repository --repository-name my-ecr-repo --region us-east-2`.
#    Replace the value of `ECR_REPOSITORY` in the workflow below with your repository's name.
#    Replace the value of `aws-region` in the workflow below with your repository's region.
#
# 2. Create an ECS task definition, an ECS cluster, and an ECS service.
#    For example, follow the Getting Started guide on the ECS console:
#      https://us-east-2.console.aws.amazon.com/ecs/home?region=us-east-2#/firstRun
#    Replace the values for `service` and `cluster` in the workflow below with your service and cluster names.
#
# 3. Store your ECS task definition as a JSON file in your repository.
#    The format should follow the output of `aws ecs register-task-definition --generate-cli-skeleton`.
#    Replace the value of `task-definition` in the workflow below with your JSON file's name.
#    Replace the value of `container-name` in the workflow below with the name of the container
#    in the `containerDefinitions` section of the task definition.
#
# 4. Store an IAM user access key in GitHub Actions secrets named `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY`.
#    See the documentation for each action used below for the recommended IAM policies for this IAM user,
#    and best practices on handling the access key credentials.

on:
  release:
    types: [created]

name: Deploy to Amazon ECS

jobs:
  deploy:
    name: Deploy
    runs-on: ubuntu-latest

    steps:
    - name: Checkout
      uses: actions/checkout@v2

    - name: Configure AWS credentials
      uses: aws-actions/configure-aws-credentials@v1
      with:
        aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
        aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
        aws-region: us-east-2

    - name: Login to Amazon ECR
      id: login-ecr
      uses: aws-actions/amazon-ecr-login@v1

    - name: Build, tag, and push image to Amazon ECR
      id: build-image
      env:
        ECR_REGISTRY: ${{ steps.login-ecr.outputs.registry }}
        ECR_REPOSITORY: my-ecr-repo
        IMAGE_TAG: ${{ github.sha }}
      run: |
        # Build a docker container and
        # push it to ECR so that it can
        # be deployed to ECS.
        docker build -t $ECR_REGISTRY/$ECR_REPOSITORY:$IMAGE_TAG .
        docker push $ECR_REGISTRY/$ECR_REPOSITORY:$IMAGE_TAG
        echo "::set-output name=image::$ECR_REGISTRY/$ECR_REPOSITORY:$IMAGE_TAG"

    - name: Fill in the new image ID in the Amazon ECS task definition
      id: task-def
      uses: aws-actions/amazon-ecs-render-task-definition@v1
      with:
        task-definition: task-definition.json
        container-name: sample-app
        image: ${{ steps.build-image.outputs.image }}

    - name: Deploy Amazon ECS task definition
      uses: aws-actions/amazon-ecs-deploy-task-definition@v1
      with:
        task-definition: ${{ steps.task-def.outputs.task-definition }}
        service: sample-app-service
        cluster: default
        wait-for-service-stability: true




pipeline{
agent any
stages{
  stage("deploy_ master"){
  when{
    branch "master"
  }
steps{
echo "hello deploy to master environment"
}
}
  stage("deploy_ dev"){
  when{
    branch "dev"
  }
steps{
echo "hello deploy to dev environment"
}
}
  stage("deploy_ uat"){
  when{
    branch "uat"
  }
steps{
echo "hello deploy to uat environment"
}
}
}
}

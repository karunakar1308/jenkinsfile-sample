pipeline {
    agent {
        label 'win_default'
    }
    tools {
        jdk 'Java 8.291'
    }
    environment {
        GIT_TOKEN = credentials('git-token')
        MAVEN_OPTS="-XX:MetaspaceSize=512m -XX:MaxMetaspaceSize=4G -Xms4G -Xmx8G -XX:+AggressiveOpts -XX:+UseConcMarkSweepGC -Dmaven.artifact.threads=20"
    }
    options {
        buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '7', numToKeepStr: '20')
        disableConcurrentBuilds()
    }
    triggers {
        bitBucketTrigger([
            [$class: 'BitBucketPPRPullRequestServerTriggerFilter', actionFilter: [$class: 'BitBucketPPRPullRequestServerCreatedActionFilter', allowedBranches: '']]
        ])
    }

config {
  daysToKeep = 21
  cronTrigger = ""
}

node() {
    catchError {
        git.checkout {
            cleanExcludePatterns = ".repository"
        }

       helm.lint {
           stage = "lint"
       }

       helm.test {
           stage = "test"
       }

       helm.pkg {
           stage = "package"
       }

       helm.upload {
           stage = "publish"
           // path is the dir in helm-local on artifactory
           path = "par-ticle/piral-feed-service"
       }
    }

    notify { slackChannel = "#par-particle-prod-alerts" }
}
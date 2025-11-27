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
// For now skip the test step, since this chart requires a license key. It wont render with the default values.yaml.
// The test step in jenkins assumes charts can be rendered with not additional values.yaml
//        helm.test {
//            stage = "test"
//        }

       helm.pkg {
           stage = "package"
       }

       helm.upload {
           stage = "publish"
           // path is the dir in helm-local on artifactory
           path = "par-ticle/feed-service"
       }
    }

    notify { slackChannel = "#par-particle-sandbox-alerts" }
}

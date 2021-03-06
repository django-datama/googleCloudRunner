# googleCloudRunner 0.3.0.9000

* Fix checking for existance of cloudscheduler.serviceAgent (#89 - thanks @BillPetti)
* Setting env vars for Cloud Run runtime deployments fixed 
* Added `cr_jwt_create()` and family to create JWTs to call authenticated services such as Cloud Run (#91)
* Add authenticated Cloud Run use case
* Ensure timeout is under 86400 secs (24hrs) in `cr_build_make()`
* Add `cr_buildtrigger_copy()`
* Extra checks for existance of valid auth file when creating build email (#89)
* We can't check for existance of cloud build email #94 so `cr_setup()` will only set roles in assumed present Google service emails.

# googleCloudRunner 0.3.0

* Move the setup wizard functions from `googleCloudRunner` to `googleAuthR` so they are available for all packages.
* Check for Cloud Scheduler Service Agent is present for scheduler to work (#73)
* `cr_build_upload_gcs()` will now clean up the files it makes when the function exits (#68 - thanks @MLud)
* Support local testing in plumber example (#66 - thanks @samterfa)
* Support multiple tags in Docker builds (#75)
* Fix being able to pass built Cloud Build objects to schedule via `cr_build_schedule_http()` (#47)
* Add progress for Cloud builds via library(progress) (#29)
* Add support for Kaniko cache in `cr_buildstep_docker()` and `cr_deploy_docker()` (#46) -should see much quicker repeat builds
* Let use of bucket level access control when using `cr_deploy_docker()`
* Added support for creating buildtriggers from R (#78)
* `cr_deploy_pkgdown()`, `cr_deploy_docker_trigger()` and `cr_deploy_packagetests()` now all have an option to create the build trigger for you
* Add `cr_deploy_badger()` for creating build badges with Cloud Build via https://github.com/kelseyhightower/badger (#15)
* Add `cr_deploy_run_website()` for rendering Rmd files then hosting on an nginx Cloud Run
* The packagetools docker updates weekly `gcr.io/gcer-public/packagetools:latest` (#55)
* Fix `cr_schedule()` crash of `overwrite=TRUE` but no existing schedule
* Add deploy Shiny to k8s and Cloud Run example use cases
* Allow max_instances in `cr_run` so it can run Shiny apps (#35)
* Add `cr_buildstep_gcloud()` for optimum gcloud builds (#83)

# googleCloudRunner 0.2.0

* Add `port` argument to Cloud Run deployments via `cr_buildstep_run()`
* Add `cr_deploy_pkgdown` and `cr_deploy_packagetests` add subsequent buildsteps to aid R package development.
* Fix `cr_buildstep_r()` so it can run R scripts from a filename when `r_source="runtime"` (#45 - thanks @j450h1 and @axel-analyst)
* Add ability to run R scripts straight from Cloud Storage (#45 - thanks @j450h1 and @axel-analyst) - specify R script location starting with `gs://`
* Let `timeout` be specified within `cr_build_yaml()` (#43 - thanks @dmoimpact)
* Correct print method for build substitutions
* Update `cr_schedule_list()` to only return non-nested data
* Allow specification of Dockerfile name in `cr_buildstep_docker()`
* Easier parsing of env arguments in `cr_buildstep()`
* Entrypoint in `cr_buildstep()` accepts one argument only
* Allow specification of timezone in `cr_schedule()` (#49 - thanks @samterfa)
* Let `cr_deploy_r()` pass through arguments to `cr_buildstep_r()` (#50 - thanks @samterfa)
* Modify `cr_deploy_packagetests()` so it can pass through dot arguments to `cr_build_yaml()` such as `timeout`
* Add `cr_buildstep_secret()` using Secret Manager (#52)
* Update `cr_deploy_pkgdown()` to use Secret Manager (#54)
* Remove unnecessary `projectId` argument from `cr_build_make()` (#57)
* Add `cr_setup()` to help setup a googleCloudRunner environment (#53)

# googleCloudRunner 0.1.1

* Initial release

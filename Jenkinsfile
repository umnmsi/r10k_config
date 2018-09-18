node {

  def rvm = "2.4.4"

  stage('Prepare') {
    checkout scm
    sh """#!/bin/bash -l
rm -f Gemfile.lock
rvm use ${rvm}@${env.BUILD_TAG} --create
gem install bundler --no-rdoc --no-ri
bundle install --without system_tests
git clone https://github.com/mbaynton/envlink.git
cd envlink/
bundle install --without system_tests"""
  }

  try {
    stage('Spec') {
      sshagent(credentials: ['75d5b2ba-a76d-4e30-aa3a-0b749b02f1cb']) {
        sh """#!/bin/bash -l
rvm use ${rvm}@${env.BUILD_TAG}
sudo -E PATH=\$PATH /bin/unshare -m /usr/local/bin/validate_r10k.sh"""
      }
    }
  } catch (err) {
    currentBuild.result = 'FAIL'
  }

  stage('Cleanup') {
    sh """#!/bin/bash -l
rvm use ${rvm}@${env.BUILD_TAG}
rvm --force gemset delete ${env.BUILD_TAG}"""
    deleteDir()
  }
}
// vim: syn=groovy ts=2 sw=2 expandtab

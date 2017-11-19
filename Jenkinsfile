#!/usr/bin/env groovy

pipeline {
	agent any
	stages {
		stage('build') {
			steps {
				sh "make build"	
			}
		}
		stage('unit-test') {
			steps {
				sh "make test"
			}
		}
		stage("advanced-tests") {
			parallel {
				stage('integration-test') {
					agent { label "build" }
					steps {
						sh "make integration"
					}
				}
				stage('acceptance-test') {
					agent { label "build" }
					steps {
						sh "make acceptance-test"
					}
				}
			}
		}
	}
}

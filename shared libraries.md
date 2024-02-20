In Jenkins, a shared library is a way to store commonly used code(reusable code), such as scripts or functions, that can be used by different Jenkins pipelines.

Instead of writing the same code again and again in multiple pipelines, you can create a shared library and use it in all the pipelines that need it. 
This can make your code more organized and easier to maintain.

Advantages
Standarization of Pipelines
Reduce duplication of code
Easy onboarding of new applications, projects or teams
One place to fix issues with the shared or common code
Code Maintainence
Reduce the risk of errors

how to write?:

1.you need to configure the jenkins to use the shared library

2.login to jenkins > managed plugins > settings > global pipeline > add the repository details and github credentials if it's private and shared library name

3.write your reusable code under vars directory
helloWorld.groovy

    def call() {
        sh 'echo Hello World'
    }

3.in Jenkins pipeline script add @Library(library name) _ as your first line

4.where ever you want to use the reusable code call that function with file name  for example helloWorld()

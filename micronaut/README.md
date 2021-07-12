# Starting with Micronaut

* 1 - [Install SDKMAN](https://sdkman.io/install)
	* curl -s "https://get.sdkman.io" | bash
	* source "$HOME/.sdkman/bin/sdkman-init.sh"
	* sdk version

* 2 - [Install micronaut](https://micronaut-projects.github.io/micronaut-starter/latest/guide/#installation)
	* sdk install micronaut 
	* (or) brew install --cask micronaut-projects/tap/micronaut

* 3 - [Create a project with mn command](https://guides.micronaut.io/latest/creating-your-first-micronaut-app-maven-java.html)
	* mn create-app example.micronaut.micronautguide --build=maven --lang=java


# Native Image Generation
* We will use GraalVM, the polyglot embeddable virtual machine, to generate a Native image of our Micronaut application.
* Native images compiled with GraalVM ahead-of-time to improve the startup time and reduce the memory footprint of JVM-based applications.
* Use of GraalVM’s native-image tool is only supported in Java and Kotlin projects. Groovy relies heavily on reflection which is only partially supported by GraalVM.
* The easiest way to install GraalVM is to use [SDKMan.io](https://sdkman.io/install).
	* For Java 8
		* sdk install java 21.1.0.r8-grl
	* For Java 11
		* sdk install java 21.1.0.r11-grl - Then restart the terminal

* You need to install the native-image component which is not installed by default.
	* gu install native-image
* To generate a native image using Maven run:
	* ./mvnw package -Dpackaging=native-image
* The native image is created in target/application and can be run with ./target/application.
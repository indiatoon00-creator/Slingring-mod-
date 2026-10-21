name: Build JAR

on:
  push:
    branches: [ "main" ]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v4

    - name: Set up JDK 17
      uses: actions/setup-java@v4
      with:
        java-version: '17'
        distribution: 'temurin'

    - name: Build with Gradle
      run: ./gradlew build

    - name: Upload JAR Artifact
      uses: actions/upload-artifact@v4
      with:
        name: my-jar-file
        path: build/libs/*.jar
        

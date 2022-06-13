# GraphScope-Java-template

## What is this

This is a Java template repo for GraphScope, By clicking `Use this template`, you will generate a new repository with the same files and structure of this template repostiory. Then you can explore your own java algorithms on GraphScope.
For more details about [GraphScope](https://github.com/alibaba/GraphScope) and the [Analytical Engine](https://graphscope.io/docs/analytics_engine.html), please visit [GraphScope web site](https://graphscope.io/). For more details of template repository, visit [official github docs](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template).

## Getting started

### Install GraphScope 

You definitely need GraphScope installed on your environment. Currently you will need to install GraphScope from source with **GRAPE-jdk** installed.

Follow [developer guide](https://graphscope.io/docs/developer_guide.html#building-and-testing-graphscope-locally-with-docker) to install GraphScope. In our case, it is ok to only install **GAE**, **client**  and **coordinator**.

```bash
cd GraphScope
make gae ENABLE_JAVA_SDK
make coordinator
make client
```

Remember to turn on flag `ENABLE_JAVA_SDK`.

### Use this template.

By click the button `User this template`, your will generate your own `GraphScope-Java-template` repository in your github accout.

Then you can clone and build the repo.

```bash
git clone https://github.com/<username>/<repo-name>.git
cd <repo-name>
cd java
mvn clean install
```

After build the maven project, a shaded-jar which contains a demo algo `Traverse` is packed into `java/target/gs-java-template-0.1.jar` along with all java classed needed to run on GAE.

To add your own algorithms, just add java classed under `jar/src/`. Refer to [API Docs](https://graphscope.io/docs/reference/gae_java/index.html) and [GAE Java Tutorials](https://graphscope.io/docs/analytics_engine.html#run-algorithm-in-java) for how to impl a graph algorithm with `GRAPE-jdk`.


### Run the app

A scirpt is provided for users to submit your java app to run on GraphScope Analytical engine.

```bash
python3 runner.py --app com.alibaba.graphscope.example.Traverse
# To provide additional arguements, use --argments
python3 ruuner.py --app ${APP_NAME} --arguements src=1
# To specify the jar you want to submit, use --jar_path
python3 runner.py --app com.alibaba.graphscope.example.Traverse --jar_path ${path_to_jar}
```


## Orgnization
- **java**: the maven project directory for your java app. Adding your own impl in this directory.
- **runner.py**: entrance to submit java app to graphscope.

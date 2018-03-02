# PlcOpen-Xml Xcore
Xcore model of the PlcOpen Xml Standard.

### Installation
Comes with maven support. The xtext-maven-plugin generates complete emf model code.
```
git clone https://github.com/MattsSe/plcopen-xml-xcore
cd plcopen-xml-xcore
mvn clean install
```

### Usage

#### Load XML
Parse a PlcOpen XML file
```java
File xmlFile = new new File("path.xml");
PlcOpenSerializer serde = new PlcOpenSerializer();
Resource plcResource = serde.loadXmlResource(xmlFile);

```

#### Write Xml
Create a model first, than save as PlcOpen XML.
```java
// build project
Project project = Tc6021Factory.eInstance.createProject();
  ...

Resource resourceSet = new ResourceSetImpl();
Resource resource = new ResourceImpl();
resourceSet.getResources().add(resource);
resource.getContents().add(project);

PlcOpenSerializer serde = new PlcOpenSerializer();
serde.writeXML(resource, "output/plcopen.xml");

```

Reading/Writing XMI models using the analogous methods of the `PlcOpenSerializer`.

See [More demos in the `PlcOpenSerializeTest` test.](src/test/java/org/plcopen/xcore/serde/PlcOpenSerializeTest.java)

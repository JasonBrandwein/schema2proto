# schema2proto  [![CircleCI](https://circleci.com/gh/entur/schema2proto.svg?style=svg)](https://circleci.com/gh/entur/schema2proto)

This tool does 2 things:

* Converts XML Schema files (.xsd) to Protocol Buffers (.proto).
* Modifies existing proto files by adding, modifying and removing fields, messages etc. Also support for merging proto
  files using the same package

### Requirments
Probably working: Java 10 or greater
working: Java 9, and Zulu 1.8

	Zulu info:
	openjdk version "1.8.0_322"
	OpenJDK Runtime Environment (Zulu 8.60.0.21-CA-win64) (build 1.8.0_322-b06)
	OpenJDK 64-Bit Server VM (Zulu 8.60.0.21-CA-win64) (build 25.322-b06, mixed mode)

### How to Build
	Have maven 3.0 or > installed.
	Go to schema2proto\schema2proto-lib
	open terminal to that location
	in terminal type:
	mvn install -DskipTests
	once the build is completed. Inside the target folder should be the .jar file that is needed to run xsd2proto commands.

## Usage

### Standalone (Only for converting XSD to PROTO)

See [standalone tool](schema2proto-lib/README.md)

### Maven (Both converting XSD to PROTO and for modifying PROTO files

See [maven plugin](schema2proto-maven-plugin/README.md)

## Maintaining backwards compatibility

If your use case is to maintain a proto descriptor based on a "living" xsd, you will need to detect and possibly resolve
any backwards incompatibility issues that may arise from modifying the xsd.

You can use the tool [protolock](https://github.com/nilslice/protolock) to verify that i.e. fields have not changed name
or id.

If you are using the Maven there is a plugin as well: https://github.com/salesforce/proto-backwards-compat-maven-plugin
 
Only automatic resolving of field name/id conflicts have been implemented so far.

## Contribution

See code style [CODESTYLE.md](CODESTYLE.md)

## Licensing

EUPL, see [LICENSE](LICENSE.txt) and https://en.wikipedia.org/wiki/European_Union_Public_Licence

The schema2proto-wire module is a modified copy from https://github.com/square/wire/tree/master/wire-schema that seems
to have become https://github.com/square/wire/tree/master/wire-library/wire-schema now.

The schema2proto-xsom module is a modified copy from https://github.com/eclipse-ee4j/jaxb-ri/tree/master/jaxb-ri/xsom,
see [original LICENSE](schema2proto-xsom/LICENSE.md)

The codebase was once based on https://github.com/tranchis/xsd2thrift but has been completely rewritten.

# Go to the source code directory
cd SE4367-ASM/src

# Compile all .java files
$ javac -cp ../lib/asm-all-6.0_BETA.jar *.java

# See the asm representation for Example.class
$ java -cp .:../lib/asm-all-6.0_BETA.jar org.objectweb.asm.util.ASMifier Example

>>>>>>>>>>>>>Parse class file>>>>>>>>>>>>>>

$ java -cp .:../lib/asm-all-6.0_BETA.jar ParseClassFile Example.class

>>>>>>>>>>>>>Generate class file>>>>>>>>>>>>>>

# Generate the Generated class file
$ java -cp .:../lib/asm-all-6.0_BETA.jar GenerateClassFile Generated.class

# Execute the generated version of Generated.class to check results
$ java -cp .:../lib/asm-all-6.0_BETA.jar Generated

>>>>>>>>>>>>>Transform class file>>>>>>>>>>>>>>

# Use CopyClassFile to copy Example
$ java -cp .:../lib/asm-all-6.0_BETA.jar CopyClassFile Example.class ExampleCopy.class

# Use ASMifier to translate ExampleTransformed into ASM representation to see what should we add to transform Example into ExampleTransformed
$ java -cp .:../lib/asm-all-6.0_BETA.jar org.objectweb.asm.util.ASMifier ExampleTransformed

# Use TransformClassFile to transform Example
$ mv Example.class Example.class.bak
$ java -cp .:../lib/asm-all-6.0_BETA.jar TransformClassFile Example.class.bak Example.class

# Execute the transformed version of Example.class to check results
$ java -cp . Example
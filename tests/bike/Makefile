all: biketest6 bike.pl product

biketest6: bike6.cpp
	g++ -O2 -I gecode-6.1.0/include -L gecode-6.1.0/lib bike6.cpp -lgecodesearch -lgecodeminimodel -lgecodeset -lgecodefloat -lgecodeint -lgecodekernel -lgecodesupport -o biketest6

biketest5: bike5.cpp
	g++ -O2 -I gecode-5.1.0/include -L gecode-5.1.0/lib bike5.cpp -lgecodesearch -lgecodeminimodel -lgecodeset -lgecodefloat -lgecodeint -lgecodekernel -lgecodesupport -o biketest5

product: Bike.java
	javac -cp choco-solver-4.10.0.jar -d . Bike.java

bike.pl: inventory.pl bike.txt
	../../fmdsl -t inventory.pl bike.txt bike.pl

bike6.cpp: inventory6.cpp bike.txt
	../../fmdsl -g6 -t inventory6.cpp bike.txt bike6.cpp

bike5.cpp: inventory5.cpp bike.txt
	../../fmdsl -g5 -t inventory5.cpp bike.txt bike5.cpp

Bike.java: inventory.java bike.txt
	../../fmdsl -c4 -t inventory.java bike.txt Bike.java

.PHONY: jshell
jshell: product
	jshell --class-path=".:choco-solver-4.10.0.jar" javasession.txt

.PHONY: gecode6
gecode6: biketest6
	time biketest6

.PHONY: clean
clean:
	-rm biketest5
	-rm biketest6
	-rm bike5.cpp
	-rm bike6.cpp
	-rm bike.pl
	-rm -rf product
	-rm Bike.java
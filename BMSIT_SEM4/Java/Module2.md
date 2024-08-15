<!--markdownlint-disable MD029-->
# String Handling

## String constructors

1. `String <name> = new String()`
2. `String <name> = new String(<insertString>)`
3. `String <name> = new String(<char array>)`
4. `String <name> = new String(<char array>,<start index>,<no of chars>)`
5. `String <name> = new String(<byte array>)`
6. `String <name> = new String(<byte array>,<start index>,<no of bytes>)`

## String length

1. `S1.length()`
2. `"<stringHere>".length()`

## String Concatenation

1. "+" operator:

    Example: "hello" + "world"
    Output : helloworld
2. `.concat()`:

    `s3 = s1.concat(s2)` or `s3 = s1.concat("xyz")`

## Character Extraction

1. `charAt()`:

    1. `char <target> = <String>.charAt(<index>)`
    2. `char <target> = <StringVariable>.charAt(<index>)`

2. `getChars()`:

    `void getChars(<startIndex>,<endIndex>,<target>,<targetStart>)`

## String Comparisions

1. `s1.equals(s2)`

    Returns True if s1 is the same object as s2
2. `s1.equalsIgnoreCase(s2)`

    Ignores case sensitivity

3. Regional Matching

    `s1.regionalMatches(<boolean IgnoreCase>,<int startIndex>,<str matchingString>,<int matchingStringStartIndex>,<int noOfChars>)`

### Difference between `==` and `equals()`

- `==` compares the objects not the values of the objects
- `equals()` compares the values of the objects

4. `compareTo()` compares ascii values

    if `s1.compareTo(s2)` is given, 0 if equal, <0 if s1 < s2 and >0 if s2 > s1

5. `compareToIgnoreCase()` same but case ignored

## Searching Strings

1. `indexOf(<int ch>)`
2. `indexOf(<string str>)`
3. `indexOf(<char ch>,<startIndex>)`
4. `indexOf(<string str>,<startIndex>)`

## Substrings

1. `.substring(<startIndex>)`
2. `.substing(<startIndex>,<endIndex>)`

## Character Replacement

`.replace(<char original>,<char replacement>)` replaces all occurances of the char with the provided one

`.trim()` removes all trailing and preceeding whitespaces

## ToString()

if the class has a toString() method, it is accessed, else the Object class's toString method is used

```java
   class A{
    int a,b;
    A(int a,int b){
        this.a = a;
        this.b = b;
    }
   } 

   public class test{
    test(){
        A c = new A(10,20);
        System.out.println(c)
    }
   }

```

This will output

`A@10b62c9` where `A` is the name of the class and the rest is the hash code

```java
   class A{
    int a,b;
    A(int a,int b){
        this.a = a;
        this.b = b;
    }
    String toString(){
        return "a="+a+"b="+b;
    }
   } 

   public class test{
    test(){
        A c = new A(10,20);
        System.out.println(c)
    }
   }

```

This will output

`a=10b=20`

## Data conversion using valueOf()

- converts from internal format to readable
- static method overloaded into String class
- overloaded for Objects to return toString() method

Eg :

```java
String str = String.valueOf(200) // "200"
```

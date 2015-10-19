Sample code ideas. 
I did a quick search for a few sample ideas, code that could easily be tested and turned into a webservice?
I'm not very familiar with RegEx, and find them obscure to maintain, but open to thoughts on these, too. Dave.

Voting/testing might begin with some of these:

[1. Tutorial ](http://www.tutorialspoint.com/javaexamples/regular_email.htm/)

[2. Java sample ](http://alvinalexander.com/blog/post/java/java-email-address-validation-class/)

[3. Using RegEx, explained ](http://www.sw-engineering-candies.com/blog-1/howtofindvalidemailaddresswitharegularexpressionregexinjava/)

[4. Best, might be pre-built utility. Why reinvent? ](http://stackoverflow.com/questions/624581/what-is-the-best-java-email-address-validation-method/)
This is the java solution...
'''java
public static boolean isValidEmailAddress(String email) {
   boolean result = true;
   try {
      InternetAddress emailAddr = new InternetAddress(email);
      emailAddr.validate();
   } catch (AddressException ex) {
      result = false;
   }
   return result;
}
'''

This is the apache commons solution...
The import:
'''java
import org.apache.commons.validator.routines.EmailValidator;
'''
The code:
'''java
String email = "myName@example.com";
boolean valid = EmailValidator.getInstance().isValid(email);
'''
and to allow local addresses
'''java
boolean allowLocal = true;
boolean valid = EmailValidator.getInstance(allowLocal).isValid(email);
'''

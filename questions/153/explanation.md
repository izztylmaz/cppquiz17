According to [lex.string]§2.14.5¶8 in the standard: "A narrow string literal has type “array of n const char”"

An array of n const char converts to a pointer to const char. According to  [conv.qual]§4.4¶1: "A prvalue of type “pointer to `cv1 T`” can be converted to a prvalue of type “pointer to `cv2 T`” if “`cv2 T`” is more cv-qualified than “`cv1 T`”." In this case however, `char*` is less cv-qualified than `const char *`, and the conversion is not allowed.

Note: While most compilers still allow `char const[]` to `char*` conversion with just a warning, this is not a legal conversion in C++11.

See also <http://dev.krzaq.cc/stop-assigning-string-literals-to-char-star-already/>
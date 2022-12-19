
# [ 스프링 용어 정리 ]

## 패키지 - 어노테이션 및 클래스 정리

### com.fasterxml.jackson.databind
```
Basic data binding (mapping) functionality that allows for reading JSON content into Java Objects (POJOs) 
and JSON Trees (JsonNode), as well as writing Java Objects and trees as JSON.
```
- ObjectMapper
> ObjectMapper provides functionality for reading and writing JSON, either to and from basic POJOs (Plain Old Java Objects), 
or to and from a general-purpose JSON Tree Model (JsonNode), as well as related functionality for performing conversions.

> [메서드]  
> **writeValueAsBytes(Object value)** : 
> Method that can be used to serialize any Java value as a byte array.  
> _(Return : byte[])_
#

### io.jsonwebtoken
- Claims
> [interface]   
> A JWT Claims set.

- Jwts
> Factory class useful for creating instances of JWT interfaces.
> Using this factory class can be a good alternative to tightly coupling your code to implementation classes.

> [메서드]  
> **claims()** : Returns a new Claims instance to be used as a JWT body.  
> _(Return: Static Claims)_  
> **builder()** : Returns a new JwtBuilder instance that can be configured
> and then used to create JWT compact serialized strings.  
> _(Return : static JwtBuilder)_

- JwtBuilder
> [interface]

> [메서드]  
> **setClaims(Claims claims)** : Sets the JWT payload to be a JSON Claims instance.  
> **setIssuedAt(Date iat)** : Sets the JWT Claims iat (issued at) value.  
> **setExpiration(Date exp)** : Sets the JWT Claims exp (expiration) value.  
> **signWith(Key key, SignatureAlgorithm alg)** :
> Signs the constructed JWT with the specified key using the specified algorithm, producing a JWS.  
> **compact()** : Actually builds the JWT and serializes it to a compact, URL-safe string according to the JWT Compact Serialization rules.

- SignatureAlgorithm
> [enum]  
> HS256, HS512 ...
#

### io.jsonwebtoken.security
- Keys
> Utility class for securely generating SecretKeys and KeyPairs.

> [메서드]  
> **hmacShaKeyFor(byte[] bytes)** :
> Creates a new SecretKey instance for use with HMAC-SHA algorithms
> based on the specified key byte array.  
> _(Return : static SecretKey)_
#

---

### java.nio.charset
```
Defines charsets, decoders, and encoders, for translating between bytes and Unicode characters.
```

- StandardCharsets
> Constant definitions for the standard Charsets.  
> ex. UTF_8, UTF_16, US_ASCII, ...
#

### java.security
```
Provides the classes and interfaces for the security framework.
```
- Key
> [interface]
> The Key interface is the top-level interface for all keys.
#

### java.sql
- Timestamp
> A thin wrapper around java.util.Date that allows the JDBC API to identify this as an SQL TIMESTAMP value.

> [메서드]  
> **from(Instant instant)** : Obtains an instance of Timestamp from an Instant object.
#

### java.time
- Instant
> This class models a single instantaneous point on the time-line. This might be used to record event time-stamps in the application.

> [메서드]  
> **now()** : Obtains the current instant from the system clock.
#

### java.util
- Date
> The class Date represents a specific instant in time, with millisecond precision.

- Optional\<T>
> A container object which may or may not contain a non-null value.

> [메서드]  
> **isPresent()** : Return true if there is a value present, otherwise false.  
> **orElseThrow(Supplier<? extends X> exceptionSupplier)** :
> Return the contained value, if present, otherwise throw an exception to be created by the provided supplier.
#

---

### javax.persistence
```
Java Persistence is the API for the management for persistence and object/relational mapping.
```

- @PrePersist
> Specifies a callback method for the corresponding lifecycle event.  
> This annotation may be applied to methods of an entity class, a mapped superclass, or a callback listener class.

- @PreUpdate
> Specifies a callback method for the corresponding lifecycle event.
> This annotation may be applied to methods of an entity class, a mapped superclass, or a callback listener class.
#

### javax.servlet
```
The javax.servlet package contains a number of classes and interfaces 
that describe and define the contracts between a servlet class and the runtime environment 
provided for an instance of such a class by a conforming servlet container.
```
- FilterChain
> A FilterChain is an object provided by the servlet container to the developer 
> giving a view into the invocation chain of a filtered request for a resource.

> [메서드]  
> **doFilter(ServletRequest request, ServletResponse response)** :
> Causes the next filter in the chain to be invoked, or if the calling filter is the last filter in the chain, 
> causes the resource at the end of the chain to be invoked.  
> _(Return : void)_

- ServletException
> [Exception]  
> Defines a general exception a servlet can throw when it encounters difficulty.

### javax.servlet.http
```
The javax.servlet.http package contains a number of classes and interfaces 
that describe and define the contracts between a servlet class running under the HTTP protocol 
and the runtime environment provided for an instance of such a class by a conforming servlet container.
```
- HttpServletRequest
> [Interface]  
> Extends the ServletRequest interface to provide request information for HTTP servlets.

- HttpServletResponse
> [Interface]  
> Extends the ServletResponse interface to provide HTTP-specific functionality in sending a response.
#

---

### lombok

- @RequiredArgsConstructor
> 필드 중 final 이나 @NotNull 이 설정된 변수를 매개변수로 갖는 생성자를 자동 생성
#

---

### org.hibernate.annotations
- @SQLDelete
> SqlDelete Annotation for overwriting Hibernate default DELETE method

- @Where
> Where clause to add to the element Entity or target entity of a collection The clause is written in SQL
#

---

### org.springframework.beans.factory.annotation
```
Support package for annotation-driven bean configuration.
```
- Autowired
> Marks a constructor, field, setter method, 
> or config method as to be autowired by Spring's dependency injection facilities.

- @Value
> Annotation used at the field or method/constructor parameter level 
> that indicates a default value expression for the annotated element.

#

---

### org.springframework.context.annotation
```
Annotation support for the Application Context, including JSR-250 "common" annotations, 
component-scanning, and Java-based metadata for creating Spring-managed objects.
```
- @Configuration
> Indicates that a class declares one or more @Bean methods
> and may be processed by the Spring container to generate bean definitions and service
> requests for those beans at runtime

- @Bean
> Indicates that a method produces a bean to be managed by the Spring container.
#

---

### org.springframework.data.jpa.repository
```
Interfaces and annotations for JPA specific repositories.
```

- JpaRepository\<T, ID>
> [Interface]   
> JPA specific extension of Repository.
#

---

### org.springframework.http
```
Contains a basic abstraction over client/server-side HTTP. 
This package contains the HttpInputMessage and HttpOutputMessage interfaces.
```

- HttpStatus
> [enum] (더 많이 있음)  
> **CONFLICT** : 409 Conflict.  
> **NOT_FOUND** : 404 Not Found.  
> **UNAUTHORIZED** : 401 Unauthorized.  
> **INTERNAL_SERVER_ERROR** : 500 Internal Server Error. 

- MediaType
> A subclass of MimeType that adds support for quality parameters as defined in the HTTP specification.

> [Fields]  
> **APPLICATION_JSON** : Public constant media type for application/json.

- ResponseEntity\<T>
> Extension of HttpEntity that adds an HttpStatusCode status code. 
> Used in RestTemplate as well as in @Controller methods.
#

---
### org.springframework.security.authentication
```
Core classes and interfaces related to user authentication, which are used throughout Spring Security.
```
- UsernamePasswordAuthenticationToken
> An Authentication implementation that is designed for simple presentation of a username and password.

> [메서드]  
> void setDetails(Object details) : (상속받은 메서드)
#

###  org.springframework.security.config.annotation
-  SecurityConfigurerAdapter
> A base class for SecurityConfigurer that allows subclasses to only implement the methods they are interested in.
#

###  org.springframework.security.config.annotation.web
- AbstractRequestMatcherRegistry\<C>
> 
#

### org.springframework.security.config.annotation.web.builders
- HttpSecurity
> A HttpSecurity is similar to Spring Security's XML <http> element 
> in the namespace configuration.
>  It allows configuring web based security for specific http requests. 
> By default it will be applied to all requests, 
> but can be restricted using #requestMatcher(RequestMatcher) or other similar methods.

> [메서드]  
> **csrf()** : Enables CSRF protection.  
> **authorizeRequests()** : Use authorizeHttpRequests() instead.  
> **authorizeHttpRequests()** : Allows restricting access based upon the HttpServletRequest using RequestMatcher implementations.  
> **sessionManagement()** : Allows configuring of Session Management.  
> addFilterBefore() :  !!
> exceptionHandling() :  !!
#

### org.springframework.security.config.annotation.web.configuration
- @EnableWebSecurity
> Add this annotation to an @Configuration class to have the Spring Security configuration 
> defined in any WebSecurityConfigurer or more likely by exposing a SecurityFilterChain bean:

- WebSecurityConfigurerAdapter
> 
#

###  org.springframework.security.config.annotation.web.configurers
- SessionManagementConfigurer
> 

- ExceptionHandlingConfigurer<H>
> 
#

### org.springframework.security.config.http
- SessionCreationPolicy
> [enum]  Specifies the various session creation policies for Spring Security.
> 
> **ALWAYS** : Always create an HttpSession  
> **IF_REQUIRED** : Spring Security will only create an HttpSession if required  
> **NEVER** : Spring Security will never create an HttpSession, but will use the HttpSession if it already exists  
> **STATELESS** : Spring Security will never create an HttpSession and it will never use it to obtain the SecurityContext

- HttpHeaders
> 
#

### org.springframework.security.core
- Authentication
> 

- AuthenticationException
> 
#

### org.springframework.security.core.context
- SecurityContextHolder
> 
#

### org.springframework.security.crypto.bcrypt
```
BCrypt implements OpenBSD-style Blowfish password hashing using the scheme 
described in "A Future-Adaptable Password Scheme" by Niels Provos and David Mazieres.
```

- BCryptPasswordEncoder
> Implementation of PasswordEncoder that uses the BCrypt strong hashing function.
#

### org.springframework.security.web
- AuthenticationEntryPoint
> 
#

### org.springframework.security.web.authentication
- UsernamePasswordAuthenticationFilter
>

- WebAuthenticationDetailsSource
> 
#

---

### org.springframework.stereotype
```
 Annotation denoting the roles of types or methods in the overall architecture
(at a conceptual, rather than implementation, level) 
intended for use by tools and aspects (making an ideal target for pointcuts).
```
- @Repository
> Indicates that an annotated class is a "Repository", originally defined by Domain-Driven Design (Evans, 2003)
> as "a mechanism for encapsulating storage, retrieval, and search behavior which emulates a collection of objects".  
> Teams implementing traditional Jakarta EE patterns such as "Data Access Object" may also apply this stereotype to DAO classes,
> though care should be taken to understand the distinction between Data Access Object and DDD-style repositories before doing so.
> This annotation is a general-purpose stereotype and individual teams may narrow their semantics and use as appropriate.
#

---

### org.springframework.transaction.annotation
```
Spring's support for annotation-based transaction demarcation. 
Hooked into Spring's transaction interception infrastructure via a special TransactionAttributeSource implementation.
```

- @Transactional
> Describes a transaction attribute on an individual method or on a class.  
> If no custom rollback rules are configured in this annotation, the transaction will roll back on RuntimeException and Error but not on checked exceptions.
#

---

### org.springframework.web.bind.annotation
```
Annotations for binding requests to controller and handler methods 
as well as for binding request parameters to method arguments.
```

- @ControllerAdvice
> Specialization of @Component for classes that declare @ExceptionHandler, @InitBinder, or @ModelAttribute methods
> to be shared across multiple @Controller classes.  
> Classes annotated with @ControllerAdvice can be declared explicitly as Spring beans or auto-detected via classpath scanning.

- @ExceptionHandler
> Annotation for handling exceptions in specific handler classes
and / or handler methods.

- @PathVariable
>

- @RequestBody
> Annotation indicating a method parameter should be bound to
the body of  the web request.
>
- @RequestMapping
> Annotation for Mapping web requests onto methods in request handling classes
with flexible method signatures.

- @RestController
> A convenience annotation that is itself annotated with
@controller and @ResponseBody

- @RestControllerAdvice
> A convenience annotation that is itself annotated with @ControllerAdvice and @ResponseBody.

- @ResponseBody
> Annotation that indicates a method return value should be bound to
the web response body.
#

### org.springframework.web.filter
- OncePerRequestFilter
> 
#

-------------------- test ---------------------
-

### org.junit.jupiter.api
```
JUnit Jupiter API for writing tests.
```
- Assertions
> Assertions is a collection of utility methods that support asserting conditions in tests.

> [메서드]  
> **assertDoesNotThrow(ThrowingSupplier\<T> supplier)** : 
> Assert that execution of the supplied supplier does not throw any kind of exception.
> If the assertion passes, the supplier's result will be returned.  
> _(Return :  static \<T> T)_  
> **assertEquals(Object expected, Object actual)** : Asserts that expected and actual are equal.  
> _(Return : void)_  
> **assertThrows(Class<T> expectedType, Executable executable)** : 
> Asserts that execution of the supplied executable throws an exception of the expectedType and returns the exception.  
> _(Return : static \<T extends Throwable> T)_  

- @Test
> @Test is used to signal that the annotated method is a test method.
#

---

### org.mockito
```
Mockito is a mock library for java - see Mockito class for for usage.
```

- ArgumentMatchers
> Allow flexible verification or stubbing.
> Mockito extends ArgumentMatchers so to get access to all matchers just import Mockito class statically.

> [메서드]  
> 
> **any()** : Matches anything, including nulls and varargs.  
> This matcher will perform a type check with the given type, thus excluding values.
> eq : !!

- Mockito
> [메서드]  
> - **when(T methodCall)** : Enables stubbing methods.   
> (Return : static \<T> OngoingStubbing\<T>)  
> Enables stubbing methods. 
> Use it when you want the mock to return particular value when particular method is called  
> Simply put: "When the x method is called then return y".
> - doThrow : 
#

---

### org.springframework.boot.test.autoconfigure.web.servlet
```
Auto-configuration for Spring MVC tests.
```
- @AutoConfigureMockMvc
> Annotation that can be applied to a test class to enable and configure auto-configuration of MockMvc
#

### org.springframework.boot.test.context
```
Classes and annotations related to configuring Spring's ApplicationContext for tests.
```
- SpringBootTest
> Annotation that can be specified on a test class that runs Spring Boot based tests. 
> Provides the following features over and above the regular Spring TestContext Framework
#

### org.springframework.boot.test.mock.mockito
```
Mockito integration for Spring Boot tests.
```
- @MockBean
> Annotation that can be used to add mocks to a Spring ApplicationContext.
#

---

### org.springframework.security.test.context.support
- @WithAnonymousUser
> When used with WithSecurityContextTestExecutionListener this annotation can be added to a test method 
> to emulate running with an anonymous user.

- @WithMockUser
> When used with WithSecurityContextTestExecutionListener this annotation can be added to a test method 
> to emulate running with a mocked user.

---

### org.springframework.test.web.servlet
```
Contains server-side support for testing Spring MVC applications.
```
- MockMvc
> Main entry point for server-side Spring MVC test support.

> [메서드]  
> **perform(RequestBuilder requestBuilder)** : 
> Perform a request and return a type that allows chaining further actions, 
> such as asserting expectations, on the result.
> _(Return : ResultActions)_  

- ResultActions
> [Interface]  
> Allows applying actions, such as expectations, on the result of an executed request.

> [메서드]  
> **andDo(ResultHandler handler)** : Perform a general action.  
> **andExpect(ResultMatcher matcher)** : Perform an expectation.
#

### org.springframework.test.web.servlet.result
```
Contains built-in ResultMatcher and ResultHandler implementations.
```
- MockMvcResultHandlers
> Static factory methods for ResultHandler-based result actions.

> [메서드]  
> **print()** : Print MvcResult details to the "standard" output stream.

- MockMvcResultMatchers
> Static factory methods for ResultMatcher-based result actions.  

> [메서드]  
> **status()** : Access to response status assertions.
#

### org.springframework.test.web.servlet.request
```
Contains built-in RequestBuilder implementations. 
Use MockMvcRequestBuilders to gain access to instances of those implementations.
```
- MockMvcRequestBuilders
> Methods in this class will reuse a MockServletContext that was created by the Spring TestContext Framework.

> [메서드]  
> post(URI uri) : Create a MockHttpServletRequestBuilder for a POST request.  
> put : !!
#
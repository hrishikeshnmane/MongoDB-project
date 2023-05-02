# Spring Security

Application Security :
- login logout
- allow/block access to URLsto logged in users
- allow/block access to URLsto logged in users AND certain roles

What Spring Security can do :
- Username / password authentication
- SSO / Okta / LDAP
- App level Authorization
- Intra app authorization : OAuth
- Microservice security (Using tokens, JWT)
- Method level security

Authentication vs Authorization ?

Authentication -
- knowledge based authentication
- possesion based Authentication:
  - phone / text messages
  - key cards and badges
  - access token devices
- multi-factor Authentication (knowledge based + possesion based)

Authorization -
- role based (entitlement)

Principle -
- currently logged in user

Roles - 
- group of authorities

Springboot advantages - 
- add mandatory authentication for URLs
- adds login form
- handles login error
- creates a user and a password 

AuthenticationManager-
- authenticate()
- responsible for authentication
- get hold of AuthenticationManagerBuilder
- Set the configuration on it

AuthenticationManagerBuilder-
- responsible to produce new AuthenticationManager (which is responsible for authentication)
- configure()

How to set a password encoder?
- just expose the @Bean of type PasswordEncoder!

Security Configuration : extends WebSecurityConfigurerAdapter
- Authentication:
    @Override
    configure(AuthenticationManagerBuilder)

- Authorization
    @Override
    configure(HttpSecurity)

Authentication Providers :
- input (Username, password) -> spring security framework puts these fields in Authentication object -> 
- AuthenticationProvider.authenticate(Authentication) {
    examines the object
    and returns Authentication object with Principle
}
- App can have muliple AuthenticationProviders
- ProviderManager implements AuthenticationManager :: authenticate() : manages providers
- providers :: supports() -> which tells whether it is a right provider
- AuthenticationProvider::authenticate() needs user details to verify against
- UserDetailsService :: loadUserByUserName() -> this is for retrieving User details to check information regarding user


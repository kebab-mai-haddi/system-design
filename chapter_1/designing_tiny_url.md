1. Requirements Engineering
Why do we need TinyURL?
- shorten the urls
- we need short urls instead of long complex ones
- something that users can also memorize for short terms
So, what does the service need to do?
1. conversion of long url to short url
2. redirecting short url to long url
3. users (signup and login)
4. url expiration

2. System Interfact
How will the users interact with the system:
- web UI (takes the input, sends to the backend and then displays the output)
- quick conversion of long to short url
- rest apis for:
    - shorten_url(long_url) -> short_url
    - validate_conversion(short_url, long_url) -> bool
    - 

3. Back of the envelope
How will the system scale?
- too many conversion calls
- too many validation calls
- sharding of urls by access
- too much conversion *repetition* (hot conversions)
- too much redirection *repetition* (hot redirections)

4. Defining data model
How will the data flow?
- backend to a service for shortening the url
- backend/shortner storing the url to database
- redirection: fetching the short url given long url from db, returning long url

database: 
key-value DB will work to store short and long urls

two DBs: lofted_db -> {long:short} and gerrard_db -> {short:long}

based on conversion
- lofted_db will be sharded to provide data locality

based on retrieval
- gerrard_db will be sharded to provide data locality

How to convert long url to short url?
26 upper case, 26 lowe case, 10 digits -> 62 numbers
- there will be hash collisions
- one-way hash (murmur hash)


another microservice
hasher
1. checks the existing url from db
2. if exists, return the shortened url
3. applies sha256 hash: h0
4. if h0 exists, provide the counter
5. return the base64 encoding

# A research on Unique Identifiers

# UUID V4

This is perhasp the most commonly utilised unique identifier among developers popularised by RFC4122, the NPM package is being downloaded 68 million times weekly.

## Features

- bundle size = 8.1 KB minified, 3.3 KB minifized + gzipped (https://bundlephobia.com/package/uuid@8.3.2)
- zero dependencies
- comes in with it's own CLI
- high security
- collision rate is low ( depending on the settings )
 
UUID is now supported in browser natively ( https://developer.mozilla.org/en-US/docs/Web/API/Crypto/randomUUID )

## Example: 

**1d6d60e0-af2f-41a8-b8b7-9be020c1f6ab**

# NanoID

Taking over UUID slowly, Nanoid is a faster alternative. It covers a wider range of alphabets and can be even run on clusters! 19M downloads weekly.

## Features

- bundle size = 869B minified, 501B minifized + gzipped (https://bundlephobia.com/package/uuid@8.3.2)
- zero dependencies
- at least twice faster than UUID
- short IDs. It uses a larger alphabet than UUID (A-Za-z0-9\_-). So ID size was reduced from 36 to 21 symbols.
- portable. Nano ID was ported to 20 programming languages.
- collision rate is low
- it uses hardware random generator. can be used in clusters.

On Github, Nanoid has more versions, updates more frequently, fewer open bugs, fewer open pull requests, and more stars.

## Example: 

**QDfI9uDW6Hm-p6zzhcoTI**

# CUID

CUID focuses on providing unique identifiers to web applications to improve horizontal scaling and sequential lookup speed. 638,000 downloads

## Features

- bundle size = 1.3kB minified, 640B minifized + gzipped (https://bundlephobia.com/package/uuid@8.3.2)
- zero dependencies
- comes with collision busting mechanism
- created by Eric Elliot ( https://www.amazon.com/gp/product/1491950293/ )
- horizontal scalibility

Today's applications don't run on any single machine.

Applications might need to support online / offline capability, which means we need a way for clients on different hosts to generate ids that won't collide with ids generated by other hosts -- even if they're not connected to the network.

Most pseudo-random algorithms use time in ms as a random seed. Random IDs lack sufficient entropy when running in separate processes (such as cloned virtual machines or client browsers) to guarantee against collisions. Application developers report v4 UUID collisions causing problems in their applications when the ID generation is distributed between lots of machines such that lots of IDs are generated in the same millisecond.

Each new client exponentially increases the chance of collision in the same way that each new character in a random string exponentially reduces the chance of collision. Successful apps scale at hundreds or thousands of new clients per day, so fighting the lack of entropy by adding random characters is a losing strategy.

Because of the nature of this problem, it's possible to build an app from the ground up and scale it to a million users before this problem rears its head. By the time you notice the problem (when your peak hour use requires dozens of ids to be created per ms), if your db doesn't have unique constraints on the id because you thought your guids were safe, you're in a world of hurt. Your users start to see data that doesn't belong to them because the db just returns the first ID match it finds.

Alternatively, you've played it safe and you only let your database create ids. Writes only happen on a master database, and load is spread out over read replicas. But with this kind of strain, you have to start scaling your database writes horizontally, too, and suddenly your application starts to crawl (if the db is smart enough to guarantee unique ids between write hosts), or you start getting id collisions between different db hosts, so your write hosts don't agree about which ids represent which data.

## Example

**ckyjcq3xg00002y6ca9p9fovr**

# ULID 

Universally Unique Lexicographically Sortable Identifier is a good unique identifier when sorting is required. 

## Features 

- bundle size = 2.5kB minified, 1.2kB minifized + gzipped (https://bundlephobia.com/package/ulid@2.3.0)
* 128-bit compatibility with UUID
* 1.21e+24 unique ULIDs per millisecond
* Lexicographically sortable!
* Canonically encoded as a 26 character string, as opposed to the 36 character UUID
* Uses Crockford's base32 for better efficiency and readability (5 bits per character)
* Case insensitive
* No special characters (URL safe)
* Monotonic sort order (correctly detects and handles the same millisecond)

Specification can be found at ( https://github.com/ulid/spec )

## Example

**01FSN7VQXZTHC8XFHZ05PSN4K2**

# KSUID 

ksuid is an efficient, comprehensive, battle-tested Go library for generating and parsing a specific kind of globally unique identifier called a KSUID. This library serves as its reference implementation.

## Features

- bundle size = 3.1kB minified, 1.5kB minifized + gzipped (https://bundlephobia.com/package/ksuid@3.0.0)
* Naturally ordered by generation time
* Collision-free, coordination-free, dependency-free
* Highly portable representations
* comes with it's own CLI


While RFC 4122 UUIDv1s do include a time component, there aren't enough bytes of randomness to provide strong protection against collisions (duplicates). With such a low amount of entropy, it is feasible for a malicious party to guess generated IDs, creating a problem for systems whose security is, implicitly or explicitly, sensitive to an adversary guessing identifiers.

To fit into a 64-bit number space, Snowflake IDs and its derivatives require coordination to avoid collisions, which significantly increases the deployment complexity and operational burden.

A KSUID includes 128 bits of pseudorandom data ("entropy"). This number space is 64 times larger than the 122 bits used by the well-accepted RFC 4122 UUIDv4 standard. The additional timestamp component can be considered "bonus entropy" which further decreases the probability of collisions, to the point of physical infeasibility in any practical implementation.

## Example

**23qadnKGcrLHYA26SZYiYyKCPJU**

# Google insights 

![image](https://user-images.githubusercontent.com/8538115/149848304-89058d53-3f4f-4acd-bfe2-6fd331d93e2e.png)

# Downloads

![image](https://user-images.githubusercontent.com/8538115/149848396-841ce70e-b04f-4410-a4ba-39c18b72de0e.png)

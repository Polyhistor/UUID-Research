# A research on Unique Identifiers

# UUID V4

This is perhasp the most commonly utilised unique identifier among developers popularised by RFC4122, the NPM package is being downloaded 68 million times weekly.

## Features

- bundle size = 8.1 KB minified, 3.3 KB minifized + gzipped (https://bundlephobia.com/package/uuid@8.3.2)
- zero dependencies
- comes in with it's own CLI
- high security
- collision rate is low

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

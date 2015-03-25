`wait` is a really small Docker utility that blocks until another container is accepting TCP connections.

Use it like this:

    $ docker run -d --name mycontainer some-image-or-other
    $ docker run --link mycontainer:mycontainer aanand/wait
    waiting for TCP connection to 172.17.0.105:5432......ok

Just link a single container to it - it doesn't matter what the link alias is.

`bashwait` is just like wait with a few changes.
docker-compose is setting 3 sets of variables for the
same ip:port combination.  also, there can be more than
one set of links. so, this little script loops through all of
the set ADDR and PORT variables and creates a long list.
then turns them into ip:port, sorts that list for uniqueness,
and then waits on each of the unique ip:port's in the
list. obvious modifications include just waiting for the
first one, and/or putting in max retries
this requites bash, cut, egrep, sed, sort and sleep.


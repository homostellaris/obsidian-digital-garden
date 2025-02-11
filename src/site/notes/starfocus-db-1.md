---
{"dg-publish":true,"permalink":"/starfocus-db-1/","title":"Starfocus offline-first database: PouchDB","tags":["buildinpublic","starfocus","database","offline-first"],"created":"2024-01-29"}
---

An essential feature for Starfocus is that it can be used when offline. When you remember something you need to do, you want to be able to get it out of your brain even if you're on the tube without reception.

I have quite a lot of experience writing web apps that follow the traditional client-server model but I haven't really ever considered the architectural differences required to support offline-first features. Once I started looking into it I was surprised how this one requirement drastically changed the flavour of technology stacks that were available to me.

I'm in the prototyping phase and after a bit of reading I settled on PouchDB. I started replacing my initial in-memory state with PouchDB but quickly found the API difficult to work with. I needed to support a reorderable list but modelling this in PouchDB become a rabbit hole in and of itself. I settled on using a special document with a JSON array to represent the list and would write some sort of query that would join on that list to get the documents. That shouldn't be so hard, right?

I quickly realised that joins were not supported in the traditional sense. Instead I had to write a 'design document' to enable use of the 'query' API which when used with the `include_docs` option would allow me to include the referenced documents. In theory this would work but I was finding this initial stab so frustrating due to other issues like there not being a hook for initialising the database. Every time I ran the code I'd got 409 conflict errors because the puts weren't idempotent. Turns out I needed to always have a reference to the existing document's revision and pass it into every query.

After a while I stopped and went back to the Googling phase to look for more modern alternatives. There has to be an easier way! More updates to come...
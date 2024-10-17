# Mental Models for Programmers

The first step to solving a problem is to express it properly. Expressing complex ideas require a _mental models_, analogies which are similar with ideas. Mental models are vital in communicating with collaborators.

This page contains a list of commonly used mental models that often serve as analogies while expressing complex ideas.

## Associations or maps 

The concept association is found everywhere in real world. Two things are associated means that they are somehow _related to each other._ For example, affixing a price tag to a product is associating the price with the product, meaning that *the product's price* is the *amount printed on the tag.*

Associations may be used for _identification_ (e.g. roll number uniquely identifies a student), for indicating _ownership_ (e.g. labels on parcels), and many other relationships. We can picture associations as arrows pointing from an object to another or from a set of objects to another.

Depending on context, an object may be associated with only one other object (one-to-one) or multiple objects (one-to-many).

Inspired by the mathematical concept of *map* (aka functions) the word map is often used instead of association: for example, the two objects are mapped to each other, a mapping exists between the objects, map this thing to that thing, etc.

### Examples

Developing an ability to identify associations in various scenarios and also expressing them is very important for a programmer.

1. In a dictionary, meanings are associated with a word (one-to-many).
2. Any ID number (e.g. roll numbers, license numbers, national IDs) is associated or mapped with a person (one-to-one).
3. A website is mapped or associated with its domain (e.g. `google.com`, `wikipedia.org`, etc.)
4. A Git local repository may be associated with one or more remotes (one-to-many).

### Associations in programming

Objects in programming languages are associative by nature. The properties of an object contain the values associated with it. For example, a student object contains only the information associated with a particular student (e.g. name, class, roll number, etc.)

The *map* data structure (called *dictionary* in some languages) is capable of storing and retrieving associations. A map variable can both associate a *key* with a *value,* and also can find the associated value given the key. The mapping rule (which key is to be associated with which value) is up to the programmer.

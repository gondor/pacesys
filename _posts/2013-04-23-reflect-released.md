---
layout: post
title: Reflect 1.0.0 Released
---

Reflect 1.0.0 was released to Maven Central today.  Reflect is a fluent reflection library in Java which cuts down all the boiler plate.  Visit the <a href="https://github.com/gondor/reflect" target="_blank">GitHub page</a> for more information.  Some high level examples are including in this post to give you a quick teaser.

### Working with Fields

**Finding All Fields**

This will return all fields from all super classes (public and private)
{:.prettyprint .lang-java}
	List<Field> fields = Reflect.on(someClass).fields().all();

**Finding All Fields based on an Annotation**

This will find all fields that have been annotated with the specified annotation in the class hierarchy.
{:.prettyprint .lang-java}
	List<Field> fields = Reflect.on(someClass).fields().annotatedWith(annotation);
		
**Matching based on a Predicate**

A predicate will allow you to control what is matched and what should be discarded during inspection. Each field found in the hierarchy will be passed to the predicate to return either a true (matched) or false to discard. The matched list will be returned.

{:.prettyprint .lang-java}
	Predicate<Field> predicate = new Predicate<Field>() {
	    public boolean apply(Field field) {
	      if (field.isEnumConstant() || someOtherEval)
	        return true;
	      return false;
	    }
	};

	List<Field> fields = Reflect.on(someClass).fields().match(predicate);
	
### Methods

The method finder has two modes in the builder chain. Each mode provides the same chained options.

{:.prettyprint .lang-java}
	// Finds static and instance based methods
	Reflect.on(someClass).methods().chain //...

	// Finds ONLY static methods
	Reflect.on(someClass).methods(true).chain //...
	
**Finding All Methods**

This will return all methods from all super classes (public and private)
{:.prettyprint .lang-java}
	List<Method> methods = Reflect.on(someClass).methods().all();
		
**Finding Methods based on an Annotation**

This will find all methods that have been annotated with the specified annotation in the current class only
{:.prettyprint .lang-java}
	List<Method> methods = Reflect.on(someClass).methods().annotatedWith(annotation);
		
**Finding a Method by Name**

{:.prettyprint .lang-java}
	Method m = Reflect.on(someClass).methods().named("getPerson");
	
### Conclusion

As you can see from the small examples above the library is easy to use and lightweight.  There is much more power behind the library than documented.  Please visit the <a href="https://github.com/gondor/reflect" target="_blank">GitHub page</a> for more information and examples. 
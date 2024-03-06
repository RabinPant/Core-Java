# Core-Java

What is the pillar of the OOPS?
1) Encapsulation
2) Abstraction
3) polymorphism
4) inheritance

```
where are you using these concept?
=> Encapsulation => within the Entity class we create a calss

```

### calendar and time-zone

```
GregorianClaendar gc = new GregorianCalendar();
sout(  gc.get(Calendar.DIFFERENT_FIELDS));
gc.setTimeZone(TimeZone.getTimeZone("America/Los_Angeles"))
TimeZone tz = gc.getTimeZone();
sout(tz.getID());
```

### Java 8 Joda Date and Time API
```

1) why new API
ans: The earlier version of Date class
Date d = new Date();

a. time was stored in millis
b. Both date and time was store in the Date class no separation
c. This date class is mutable 
New has:
a. LocalDate
b. LocalTime
c. LocalDateTime
LocalDate is immutable class
It has separate Date and Time
It sotres time in seconds and nano-seconds

Date d = new Date();
d.setHours(21);
sout(d);

LocalDate dt = LocalDate.now();
sout(dt);

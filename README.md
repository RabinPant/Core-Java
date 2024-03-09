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
System.out.println(System.currentTimeMillis()/1000/60/60/24/365);
Date d = new Date();
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
```
### Collectin framework
```
add()/ addAll()/ remove()/removeAll()/clear()/isEmpty()/ contains()/containesAll()/equals()/size()/iterator()/toArray()

List => add(int index, E e)/ addAll()/remove()/get(int index)/set(int index, E e)/subList(int from, int to)/ indexOf(Object o)/ lastIndexOf(Object o)

Queue => FIFO /add()/ poll(removes first element from the queue)/ peek()/ remove() throws NoSuchElementException

Iterator<Integer> it = al1.iterator();
        while(it.hasNext()){
            System.out.println(it.next());
        }

Linked list and Array list in code there is one difference:
LinkedList<Integer> l1 = new LinkedList<>();
        l1.addFirst(1);
        l1.addLast(2);
        l1.peek() =>  to ge the element
        for(Integer a:l1){
            System.out.println("Linked" + a);
        }
ALthough in the core structure there are many difference

LinkedHashMap<Integer,String> lhm = new LinkedHashMap<>(5,0.75f,true);
When we use this then most recently access data will come at the bottom and lest access will go top.
if you want to implement CACHE where after 5 data least acess data is removed then.

LinkedHashMap<Integer,String> lhm = new LinkedHashMap<>(5,0.75f,true){
            @Override
            protected boolean removeEldestEntry(Map.Entry eldest) {
                return size()>5;
            }
        }
```
### Interview Questions
```
ArrayList<Emp> emps = new ArrayList<>();
        emps.add(new Emp("rabin","5802359696",12));
        emps.add(new Emp("abin","5802359696",22));
        emps.add(new Emp("sabin","5802359696",1));
        emps.add(new Emp("pabin","5802359696",18));

//        I have two choice fist one is using comparable and second is comparator.
//        comparable can be use in only one logic whereas comparator can be use in multiple
        Collections.sort(emps);
        System.out.println(emps);
        Collections.sort(emps,new Sort());
        System.out.println(emps);
```

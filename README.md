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


..................................................
1) What collections you used in project?
I used List, Set and map. Under it I have used ArrayList, linkedList, HashSet, LinkedHashSet, and TreeSet. In map I have used HashMap,LinkedHashMap, and TreeMap.

Under Java.util.concurrent.* I have used copyOnWriteArrayList, CopyOnWriteArraySet and ConcurrentHashMap.

2) Difference between, List -> set , ArrayList, LinkedList
Declaring List as a final :
final List<String> a = new ArrayList<>();
        a.add("ra");

3) we can declare list as final and add data but can't reassign a = new ArrayList<>();

4) How can I write custom ArrayList where duplicate is not allowed?
public class CustomArrayList extends ArrayList {

    @Override
    public boolean add(Object o){
        if(this.contains(o)){
            return true;
        }else{
            return super.add(o);
        }
    }
    public static void main(String[] args) {
        CustomArrayList list = new CustomArrayList();
        list.add(1);
        list.add(1);
        list.add(1);
        list.add(2);
        System.out.println(list);
    }

5) why set doesn't allow unique element?
Set<String> s = new HashSet<>();
s.add(1);

//Internal implementatio of SET add method
public boolean add(E e) {
        return map.put(e, PRESENT)==null;
    }

Its because internally set make use of map and whatever value we pass through add method of set it's put in that map as key and the value is PRESENT which is actally a dummy value.

6) In what scenario does the set method allows the duplicate and how can we prevent it?
Whenever we're using a custom object or any wrapper class then at that time the set allows the duplicate to prevent this scenario we have to make use of the equals() and HashCode() method in the custom class.

 @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Emp emp = (Emp) o;
        return empId == emp.empId && Objects.equals(name, emp.name) && Objects.equals(phone, emp.phone);
    }

    @Override
    public int hashCode() {
        return Objects.hash(name, phone, empId);
    }

7) Difference between Comparable and Comparator

9) Difference between fail fast and fail safe iterator

 A iterator which will fail fast when we do any modification while iterating a collection is called fail fast iterator. (AraryList, HashMap and vector)
This is the error we get if we use this:
 List<String> list = new ArrayList<>();
        list.add("1");
        list.add("2");

        Iterator<String> iterator = list.iterator();
        while(iterator.hasNext()){
            String next = iterator.next();
            System.out.println(next);
            list.add("2");
Exception in thread "main" java.util.ConcurrentModificationException
	at java.util.ArrayList$Itr.checkForComodification(ArrayList.java:909)
	at java.util.ArrayList$Itr.next(ArrayList.java:859)
	at practise.main(practise.java:15)

Iterator who allows us to modify in middle while iterating a collection is called Non-Fail fast iterator. ex (copyOnWriteArrayList,CopyOnWriteArraySet, ConcurrentHashMap)

10) What is the need of ConcurrentHashMap and how it is different from HashMap?

HashMap				ConcurrentHashMap
non-synchronized		synchronized
not thread-safe			thread-safe
fail-fast and throws		fail-safe and performs iteration by multiple threads
exception		
faster
you can put null value			slower than hashmap/can't put null value


** HashMap applies lock on the entire map object whereas the concurrentHashMap will applies lock only on segment level.

*** If we have HashTable which is already synchronized then why we need ConcurrentHashMap?
Locking mechanism still same as per HashMap(lock whole underlying DS)

**** we can synchronize a hashmap using collections then why can't we use that instead using concurrentHashMap?
if we use Collectios.synchronizedMap(map) it will act as synchrnized hashtable where again locking mechanism is different.

How can we achieve thread safety?
By adding Synchronization keyword
volatile
atomic variable
final keyword



How hashMap works internally:
Why HashMap keys are immutable?



= Garbage collection in java automatically frees memeory by removing objects that are no longer used. It frees the memory by unused objects, making space for new objects.

=> The finalize() method is called by garbage collector on an object when it determines that there are no more refrences to the object. It's meant to give the object a chance to clean up resources before its collected.
=> JVM uses multiple garbage collection 
```

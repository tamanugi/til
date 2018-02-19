```java
class Person {
  private String name;
  private String hobby;
  
  Person(String name, String hobby){
    this.name = name;
    this.hobby = hobby;
  }
  
  public String getName(){
    return this.name;
  }
  
  public String getHobby(){
    return this.hobby;
  }
}

    Person p1 = new Person("hoge", "running");
    Person p2 = new Person("hogehoge", "videogame");
    Person p3 = new Person("fuga", "running");
    Person p4 = new Person("fugafuga", "tennis");
    
    List<Person> list = new ArrayList<>();
    list.add(p1);
    list.add(p2);
    list.add(p3);
    list.add(p4);
    
    // hobbyの値でグルーピング
    list.stream().collect(Collectors.groupingBy(Person::getHobby))
    
    // keyの順番を保持する
    list
    .stream()
    .collect(Collectors.groupingBy(
                        Person::getHobby,
                        LinkedHashMap::new,
                        toList()
                ));

    // 以下のコードと同じ
    Map<String, List<Person>> res = new LinkedHashMap<>();
    for (Person p : list) {
        res.computeIfAbsent(p.getHobby(), k -> new ArrayList<>()).add(p);
    }
```
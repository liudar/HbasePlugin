# HbasePlugin
hbase数据库的工具类

### 添加依赖
下载项目, 运行maven的install命令然后添加依赖
```Java
     <dependency>
            <groupId>com.echo</groupId>
            <artifactId>HbasePlugin</artifactId>
            <version>1.1</version>
     </dependency>
```

### 添加配置
`/config/hbase.config` `resource/hbase.config`
```
zookeeper_quorum=bd103.hadoop.com,bd101.hadoop.com,bd102.hadoop.com
zookeeper_port=2181
znode_parent=/hbase-unsecure

```


### 自定义数据类
```Java
@Table("person")
public class Person extends HbaseEntity {
    @Column("d:name")
    public String name;

    @Column("d:age")
    public int age;

    @Family("d")
    @Column("sex")
    public int sex;

    //自定义 Hbase 中的key
    @Override
    public byte[] getKey() {
        return super.getKey();
    }
}
```
```Java
@Table("person")
@Family("d")
public class Person extends HbaseEntity {
    //默认column和属性相同
    public String name;
    public int age;
    public int sex;

    //自定义 Hbase 中的rowkey
    @Override
    public byte[] getKey() {
        return super.getKey();
    }
}
```

### 查询数据
```Java
//这个类中定义了一些常用的方法, 也可以自己添加方法
Table<Person> table = new Table(Person.class);
//通过rowkey获取数据
Optional<Person> person = table.get(null);

System.out.println(person.get().name);
```


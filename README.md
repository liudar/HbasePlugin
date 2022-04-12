# HbasePlugin
hbase数据库的工具类

基本使用
1. 直接使用jar

2. 添加依赖
<dependency>
            <groupId>com.echo</groupId>
            <artifactId>HbasePlugin</artifactId>
            <version>1.1</version>
</dependency>


自定义类;

`你好`
`你好`
`你好`


``@Table("person")
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
}``


# 利用枚举类来去除工厂类里的大量switch case语句

```java
class Woman extends User {
    public Woman() {
        System.out.println("woman");
    }
}

class Man extends User {
    public Man() {
        System.out.println("man");
    }
}

class Test {
    public static void main(String[] args) {
        for (SexEnum sex : SexEnum.values()) {
            if (sex.equals(SexEnum.MAN)) {
                sex.getUser();
            }
        }
    }
}

public enum SexEnum {
    MAN(1) {
        public User getUser() {
            return new Man();
        }
    },
    WOMAN(2) {
        public User getUser() {
            return new Woman();
        }
    };

    private final int symbol;

    SexEnum(int symbol) {this.symbol = symbol;}

    public int getSymbol() {return symbol;}

    public abstract User getUser();
}
```

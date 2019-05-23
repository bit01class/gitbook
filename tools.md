# tools

### advanced REST client

[advanced REST client](https://chrome.google.com/webstore/detail/advanced-rest-client/hgmloofddffdnphfgcellkdfbfbjeloo)

## Nexus

[Download](https://www.sonatype.com/download-oss-sonatype)

* nexus 3.x
  * Nexus Repository Manager 어플리케이션 폴더
* sonatype-work
  * Data-store로 저장소, 설정, 캐시 등의 모든 데이터가 이 폴더 하위에 저장

Run

* UNIX

```text
./nexus run
```

* WINDOW

```text
nexus.exe /run
```

login

```text
admin / admin123
```

[https://confluence.curvc.com/pages/viewpage.action?pageId=20251565](https://confluence.curvc.com/pages/viewpage.action?pageId=20251565)



### Maven





#### maven properties

```markup
<properties>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    <maven.compiler.source>1.7</maven.compiler.source>
    <maven.compiler.target>1.7</maven.compiler.target>
</properties>
```



#### maven test pass 

```markup
<plugin>
  <groupId>org.apache.maven.plugins</groupId>
  <artifactId>maven-war-plugin</artifactId>
    <configuration>
      <failOnMissingWebXml>false</failOnMissingWebXml>
    </configuration>
</plugin>

```

```bash
mvn -Dmaven.test.skip=true pakage

```




















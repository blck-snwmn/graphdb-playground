作成
```
CREATE (:User{name:"AA"});
CREATE (:User{name:"BB"});
CREATE (:User{name:"CC"});
CREATE (:User{name:"DD"});
CREATE (:User{name:"EE"});
CREATE (:User{name:"FF"});
CREATE (:User{name:"GG"});
MATCH (a:User{name:"AA"}),(b:User{name:"BB"}) CREATE (a)-[:Cracker{count:5}]->(b);
MATCH (a:User{name:"AA"}),(b:User{name:"BB"}) CREATE (a)-[:Cracker{count:3}]->(b);
MATCH (a:User{name:"AA"}),(b:User{name:"BB"}) CREATE (a)-[:Cracker{count:1}]->(b);
MATCH (a:User{name:"BB"}),(b:User{name:"CC"}) CREATE (a)-[:Cracker{count:1}]->(b);
MATCH (a:User{name:"CC"}),(b:User{name:"DD"}) CREATE (a)-[:Cracker{count:1}]->(b);
MATCH (a:User{name:"AA"}),(b:User{name:"DD"}) CREATE (a)-[:Cracker{count:1}]->(b);
MATCH (a:User{name:"GG"}),(b:User{name:"FF"}) CREATE (a)-[:Cracker{count:2}]->(b);
MATCH (a:User{name:"FF"}),(b:User{name:"EE"}) CREATE (a)-[:Cracker{count:5}]->(b);
MATCH (a:User{name:"DD"}),(b:User{name:"CC"}) CREATE (a)-[:Cracker{count:2}]->(b);
MATCH (a:User{name:"AA"}),(b:User{name:"GG"}) CREATE (a)-[:Cracker{count:3}]->(b);
MATCH (a:User{name:"AA"}),(b:User{name:"FF"}) CREATE (a)-[:Cracker{count:3}]->(b);
MATCH (a:User{name:"FF"}),(b:User{name:"AA"}) CREATE (a)-[:Cracker{count:3}]->(b);
MATCH (a:User{name:"DD"}),(b:User{name:"FF"}) CREATE (a)-[:Cracker{count:3}]->(b);
```

検索
```
MATCH (n) RETURN n; 
MATCH (a:User{name:"AA"}) RETURN a;
MATCH (a:User{name:"AA"})-[r]->(b) RETURN a, r, b;
MATCH (a:User{name:"AA"})-[r:Cracker]->(b) RETURN a, sum(r.count), b;
```

削除
```
MATCH ()-[r]->() DELETE r;
MATCH (n) DELETE n;
```

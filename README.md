# Connector config

| property name                                   | value                                        | description                                                                     |
|-------------------------------------------------|----------------------------------------------|---------------------------------------------------------------------------------|
| connector.class                                 | io.debezium.connector.mysql.MySqlConnector   |                                                                                 |
| tasks.max                                       | 1                                            | 각각의 커넥터 인스턴스가 실행할 수 있는 작업의 수                                                    |
| database.hostname                               | database Host                                |                                                                                 |
| database.port                                   | database port                                |                                                                                 |
| database.user                                   | database username                            |                                                                                 |
| database.password                               | database password                            |                                                                                 |
| database.allowPublicKeyRetrieval                | true                                         |                                                                                 |
| database.server.name                            | CDC-ORDER-CONNECTOR                          | server name (alias)                                                             |
| database.include.list                           | ORDER                                        | 캡처에 포함시킬 데이터베이스명 (comma 로 이어쓰기 가능)                                              |
| database.history.store.only.captured.tables.ddl | true                                         | 캡처 대상 테이블에서만 ddl 변경사항 수신 여부                                                     |
| database.history.skip.unparseable.ddl           | true                                         | 구문오류에 해당하는 ddl문 파싱에러시 skip 여부                                                   |
| database.history.kafka.bootstrap.servers        | kafka broker host                            |                                                                                 |
| database.history.kafka.topic                    | CDC-ORDER-CONNECTOR-SCHEMA                   | 스키마 변경 내용에 대한 토픽                                                                |
| table.include.list                              | ORDER.outbox                                 | 캡처할 테이블 (comma 로 여러개 가능)                                                        |
| include.schema.changes                          | false                                        | 스키마명과 동일한 이름을 가진 카프카 토픽으로 스키마 변경사항을 발행할지 여부                                     |
| snapshot.mode                                   | schema_only                                  | 기본값 initial 은 저장 된 모든 데이터를 읽음                                                   |
| snapshot.locking.mode                           | none                                         | 기본값 minimal 은 스냅샷을 찍기 위해 global lock 을 잡아버림                                     |
| value.converter                                 | org.apache.kafka.connect.json.JsonConverter  |                                                                                 |
| value.converter                                 | org.apache.kafka.connect.json.JsonConverter  |                                                                                 |
| value.converter.schemas.enable                  | false                                        | schema 정보 포함 여부 (스키마 기반의 직렬화 사용 여부)                                             |
| transforms                                      | unwrap                                       | Envelope -> payload 형태로 전환 (schema, payload 중 변경 된 데이터의 schema 정보는 포함시키지 않기 위함) |
| transforms.unwrap.type                          | io.debezium.transforms.ExtractNewRecordState |                                                                                 |
| transforms.unwrap.drop.tombstones               | false                                        | 삭제 된 데이터를 카프카에서도 지울건지 여부                                                        |
| transforms.unwrap.add.fields                    | op                                           | payload 정보에 op (c,r,u,d action) 정보 추가, prefix 를 별도로 지정하지 않는경우 "__op" 와 같이 발행됨   |

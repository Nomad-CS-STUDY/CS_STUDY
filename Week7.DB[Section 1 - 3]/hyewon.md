## MIZ

### Key의 개념과 종류 3가지 설명해주세요

Key는 테이블 간의 관계를 좀 더 명확하게 하고 테이블 자체의 인덱스를 위해 설정된 장치입니다. 키는 기본키, 외래키, 후보키가 있습니다. 기본키는 PK라고 부르며, 중복되는 값이 없으며 최소 필드만 써서 키를 형성할 수 있습니다. 기본키는 중복된 값을 제외하며 중복되지 않는 것은 자연스레 뽑다가 나오는 키나 인위적으로 생성한 키 중에 골라 설정합니다. 외래키는 FK라고 부르며, 다른 테이블의 기본키를 그대로 참조하는 값으로 개체와의 관계를 식별하는데 사용하는데 중복되어도 괜찮습니다. 후보키는 기본키가 될 수 있는 후보들이며 유일성과 최소성을 동시에 만족하는 키입니다.

### Isolation level의 필요성에 대해 설명해주세요

Isolation level은 격리수준으로 트랜잭션의 ACID 특성을 보장하기 위해서 사용합니다. 데이터베이스는 트랜잭션이 독립적인 수행을 하도록 합니다. 따라서 Locking을 통해, 트랜잭션이 DB를 다루는 동안 다른 트랜잭션이 관여하지 못하도록 막는 것이 필요합니다. 무조건 Locking으로 동시에 수행되는 수많은 트랜잭션들을 순서대로 처리하는 방식으로 구현하게 되면 데이터베이스의 성능은 떨어지게 될 것입니다. 그러나 그렇다고 해서 성능을 높이기 위해서 Locking의 범위를 줄인다면, 잘못된 값이 처리될 문제가 발생하게 됩니다. 따라서, 효율적인 Locking 방법이 필요합니다.

---

## js

### ACID 중 원자성(atomiciy)에 대해 설명해 주세요.

원자성은 트랜잭션과 관련된 일은 모두 실행되던지 모두 실행되지 않도록 하던지를 보장하는 특성입니다. 즉, 일부만 실행하는 것이 불가능하다는 것이죠. 그러므로 트랜잭션 내의 모든 작업이 성공적으로 완료되거나, 어느 하나라도 실패할 경우 모든 작업이 롤백되어 이전 상태로 복원됩니다.

### ACID 중 일관성(consistency)에 대해 설명해 주세요.

일관성은 트랜잭션 작업 처리의 결과가 항상 일관되어야 한다라는 뜻을 가지고 있습니다. 동일한 데이터가 여러 파일에 흩어져 있으므로, 작업 후 동일한 데이터가 서로 다른 값을 가지는 상태는 작업 처리 결과가 일관되게 적용되지 않은 것으로 일관성이 유지되지 않아 무결성의 문제가 생긴 상황입니다. 그러므로 작업 처리 후, 여러 파일의 동일한 데이터가 동일한 값을 가져야 일관성이 보장되며 무결성이 보장됩니다.

---

## yeop222

### ERD에 대해 설명해주세요.

ERD는 데이터베이스를 구축할 때 가장 기초적인 뼈대 역할을 하며, 릴레이션 간의 관계들을 정의하는 것으로 시스템의 요구 사항을 기반으로 작성되며 이 ERD를 기반으로 데이터베이스를 구축합니다. 개체 관계도라고도 불리며 요구분석사항에서 얻은 엔티티와 속성들의 관계를 그림으로 표현한 것입니다.

### 정규화 과정에 대해서 설명해주세요.

정규화 과정은 릴레이션 간의 잘못된 종속 관계로 인해 데이터베이스 이상 현상이 일어나서 이를 해결하거나, 저장 공간을 효율적으로 사용하기 위해 릴레이션을 여러 개로 분리하는 과정입니다. 정규화 과정은 정규형 원칙을 기반으로 정규형을 만들어가는 과정입니다. 정규형 원칙은 총 4가지 입니다. 첫 번째, 같은 의미를 표현하는 릴레이션이지만 좀 더 좋은 구조로 만드는 것입니다. 두 번째, 최소한의 중복성을 고려해야하는 것입니다. 세 번째, 독립적인 관계는 별개의 릴레이션으로 표현해야 하는 것입니다. 마지막은 각각의 릴레이션은 독립적인 표현이 가능해야 하는 것입니다.

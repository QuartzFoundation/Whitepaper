<h1 align="center">Quartz Framework</h1>
<h2 align="center">A Framework for Blockchain Scalability</h2>
<p align="center">
author <a href="mailto:ys.choi@me.com">Yoonsung Choi</a>
</p>

<p align="center">
  <a href="https://github.com/QuartzWorld/Whitepaper"><img src="https://badge.fury.io/gh/QuartzWorld%2FWhitepaper.svg" /></a>
  <a href="https://github.com/QuartzWorld/Whitepaper/blob/master/LICENSE"><img src="https://img.shields.io/badge/License-LGPL%20v3-blue.svg" alt="License: LGPL v3" /></a>
</p>

## Abstract

이 문서는 Blockchain의 초당 Transaction 처리 속도를 자체적인 경제 모델과 연계한 Quartz Framework라고 불리는 프로토콜 집합체를 설명하고 있습니다. 이 Framework가 가지는 Proof of Stake는 투표량에 따라, Validator들이 받게되는 수수료를 달리 하는 경제적 구조를 통해 Transaction Bandwidth를 결정하게 합니다. 

또한 이 Framework는 Ethereum[[1]](https://github.com/ethereum/wiki/wiki/White-Paper)과 연계되어 작동하며, 이용자들은 Transaction 수수료를 Ether로 지불하지 않고 자체적인 Token을 이용하여 행동에 대한 수수료를 납부할 수 있습니다. 이러한 작동방식에 따라 Quartz Framework를 통해 파생되는 Network들은 개별적인 Cryptoeconomy를 확립하게 됩니다.


## Background

현재의 Blockchain은 Block의 용량적 제한 그리고 처리 단위에 대한 제한으로 전 세계에서 동시 다발 적으로 발생하는 Transaction을 다수 처리할 수 없으며, 현재 처리되는 Transaction은 수수료가 높은 순서대로 처리됩니다.

이러한 상황에서 Transaction 처리 비율과 네트워크의 안정성 향상을 위해서 GHOST Protocol[[7]]()이 도입되지만, 현재의 Proof of Work에서 Transaction을 병렬적으로 처리하기 위한 주 요인이 되지 못합니다.

Blockchain은 다양한 이용자들이 사용하는 공용 플랫폼이며, 다수의 Transaction이 발생합니다. 이러한 Transaction은 제한된 크기의 Block에 담겨야 처리된 것으로 간주합니다. Initial Coin Offering과 같은 이벤트가 Blockchain에서 발생하는 경우, Block에 Transaction을 포함하기 위해 전체적으로 Transaction 수수료가 상승하게 됩니다. 이러한 이벤트에 참여하지 않는 다수의 이용자들도 평균적으로 상승하는 수수료에 맞춰 지불하게 됩니다.

Blockchain 상에서 다양한 자산들이 Token 형태로 발행되었으며, 이것들은 Coin과 다르게 이용 방법과 가치가 각각 다릅니다. 하지만 이러한 Token을 전송하거나, 이용할 때는 주 Blockchain이 제공하는 Coin을 이용하여 Transaction 수수료를 지불하여야 하는 단점이 존재합니다. [EIP-865](https://github.com/ethereum/EIPs/issues/865)이나 [EIP-1077](https://eips.ethereum.org/EIPS/eip-1077)은 Token을 Transaction 수수료로 지불할 수 있도록 하였으나, 이는 근본적으로 타인을 통한 Transaction 처리이기 때문에 근본적인 해결 방법은 되지 못합니다.


## Introduction

Ethereum과 Bitcoin을 비롯하여 Blockchain은 상태를 저장하고, 변경의 기록을 Block에 담아 모든 Peer to Peer 네트워크를 통해 참여자들이 동일하게 가지게 됩니다. 또한 Smart Contract의 발전으로 Blockchain의 상태 변경을 프로그램 할 수 있게 되었고, 이를 통해서 중재자 없는 다양한 서비스들이 세상에 나올 수 있게 되었습니다.

하지만 이 모든 서비스들의 Transaction을 처리하기에는 Blockchain이 수용할 수 있는 초당 Transaction 처리 수가 너무 낮다는 것이 문제입니다. Blockchain의 Scalability를 해결하는 것은 너무 오랜 연구시간을 요구합니다.

Block 보상으로 채굴자에게 주어지는 암호 화폐를 Coin, Blockchain을 기반으로 만들어진 암호 화폐를 Token이라 부르는데, Decentralized Application(이하 DApp)을 이용하기 위해서는 Token이 주요한 경제적 요인을 가지고 작동하게 됩니다. 하지만 이를 이용하기 위해서는 수수료로 Coin 또한 필요로 하게 됩니다.

대부분의 DApp은 Coin를 수수료로 지불하여 Token을 사용하도록 하는데, 이는 필수적으로 Coin을 필요로 한다는 문제가 있습니다. 그렇다면 상태의 전이만 처리하는 Off-chain의 경우, Coin없이 Token의 지불이 가능할 것입니다. 하지만 Off-chain은 상태가 저장되지 않고, 암호 작업에 많은 리소스를 투입하게 됩니다.

결론적으로 상태의 처리에 대한 것은, 다음과 같은 극단으로 나뉘게 됩니다.

* Blockchain을 통해서 전체 State를 간단히 추적하는 방법
* 많은 암호 작업을 통해서 나의 State의 추적하는 방법

Quartz는 이러한 극단에서 장점만을 취한 Framework입니다. 이를 통해 생성된 Network는 기본적으로 Ethereum에 연결되어 있지만, Ethereum의 Off-chain으로 작동합니다. 이 네트워크는 ERC-20 기반의 Token들을 통해서 자율적인 경제 체계를 가지고, 다수의 Transaction을 자체적으로 처리할 수 있게 됩니다.

다음과 같은 사용 사례들이 존재할 수 있습니다.

* 법정화폐를 기반으로 하는 Point of Sales System Network
* Multi-Party Computation
* Ticketing / Ticket Trade Platform
* Consortium Blockchain


## Quartz Framework

Quartz Framework는 다음과 같은 목적을 위해 연구되었습니다.

- <b> Blockchain for DApp </b> - Ethereum 위에 DApp을 개발하게 되면, DApp의 Transaction은 다른 Transaction과 동등하게 취급되어, 수수료를 많이 담고 있는 순서대로 처리되게 됩니다. 그렇다면 특정 Smart Contract또는 Contract의 집합(DApp)을 위한 Blockchain이 존재한다면, 모든 작동을 해당 DApp을 사용하는 이용자들에게 적용됩니다. 결과적으로 Ethereum은 모든 Transaction을 처리하지 않아도 되므로, 주 Blockchain의 Transaction 수용률이 증가하게 됩니다. 

- <b> 경제적 독립 </b> - 현대의 DApp을 이용하기 위해서는 각 DApp에서 발행한 Token 이외에, 주 Blockchain의 재화를 Transaction 수수료로 지불하여야 합니다. 그러나 Quartz Framework는 ERC-20 기반의 Token을 수수료와 Cryptoeconomy를 가집니다. 네트워크의 이용 수수료는 Token으로 지불하고, Validator들은 이 수수료를 수수하는 것으로 네트워크를 유지하게 됩니다. 이러한 접근 방법은 네트워크의 가치를 판단하는데 유용하며, 좀 더 나은 사용자 경험을 제공합니다.

- <b> 새로운 합의 알고리즘 </b> - 각 DApp의 원활한 작동을 위해서 Transaction 수용률은 높으면 높을 수록 좋습니다. 즉 Transaction 수용률이 높으면 많은 사용자들을 수용할 수 있다는 것과 같습니다. 그러기 위해서 초당 Transaction 처리율(이하 tps)을 극도로 끌어올려야 합니다. 그러기 위해서 새로운 경제 모델을 도입한 새로운 합의 알고리즘에 대한 연구를 필요로 합니다.

- <b> Ethereum의 대량 채택 </b> - 현재의 Ethereum은 모든 Node가 Transaction을 o(c)의 속도로 계산하게 됩니다. 이는 Light Client로 작동하는 IOT Device, Smart Phone에게 배터리나, 연산능력 그리고 Blockchain은 용량에 치명적입니다. 또한 다른 Node를 신뢰하여야 한다는 점 때문에 네트워크의 대역폭을 지속적으로 사용합니다. 이는 Ethereum이 채택되기 어려운 환경이며, 이러한 문제를 해결할 수 있는 방법이 고려되어야 합니다.

위와 같은 이유로 Quartz Framework를 구현하려고 하며, 이는 다음과 같은 기능을 제공하여 최종 사용자에게 극도로 최적화된 사용자 경험을 제공

- <b> Time based Block </b> - 현재 존재하는 많은 Consensus Algorithm은 일종의 대표자를 선출하여 Block을 생성하게 합니다. Quartz Framework는 대표자를 선출하게 하지 않고 이미 물리적으로 존재하며, 비 가역적인 시간을 이용하여 Block을 생성합니다. 모든 참여 Node는 해당 시간 간극만큼 주기적으로 Block을 추적하고 Transaction을 Block에 담게 됩니다. 이는 일종의 Key Block을 생성하고, 이후에 Micro Block을 모으는 Bitcoin-NG[[2]](https://www.usenix.org/system/files/conference/nsdi16/nsdi16-paper-eyal.pdf)와 유사합니다. 다만 Bitcoin-NG의 선출 과정이 시간에 의해 존재하지 않게 되었고, Block은 시간을 표방하기 때문에, 즉각적인 최종성을 획득할 수 있습니다.

- <b> Proof of Stake </b> - Proof of Stake는 Practical Byzantine Fault Tolerance[[3]](http://pmg.csail.mit.edu/papers/osdi99.pdf)의 구현으로 Block에 66.7% 이상의 투표율을 가져야 Block이 최종성을 띠며 네트워크가 공격에 대한 저항성이 생깁니다. 모든 Validator는 시간을 기반으로하는 Block에 투표를 할 뿐이며, 모든 이용자들은 투표 내역에 따라서 Transaction을 개별적으로 처리하게 됩니다.

- <b> Sharding & Light Client </b> - 모든 이용자들은 특정 Smart Contract만을 추적할 수 있으며, Validator가 투표한 내역에 따라서 해당 Smart Contract의 Merkle Root를 가지고, 다른 이용자와 동기화 할 수 있습니다. 이는 이용자가 특정 Transaction만 처리하여야 하는 동기를 제공하며, 모든 Block의 데이터 복제는 이용자들 사이에 분산되어 있습니다.

- <b> Own Cryptoeconomy </b> - 각 DApp을 이용하기 위해서 발행된 Token을 Transaction 수수료로 지불하고, Validator는 수수료를 얻기 위해서 Block에 투표하게 됩니다. Validator는 담보된 Token에 따라 투표권을 얻으며, 전체 투표량에 따라 Transaction이 처리됩니다. 이는 일종의 Transaction 수수료 확률 게임입니다. Transaction을 생성하는 이용자들은 최저한의 수수료를 베팅하고, Validator들은 이 수수료를 취하기 위해서 최대한 투표를 진행하게 됩니다. 투표가 100%에 가까워지면 모든 Transaction의 수수료를 취할 수 있으며, 반대로 투표가 0%에 가깝다면 수수료를 취할 수 없을 것입니다. 만약 Transaction을 빠르게 처리하기 위해서 많은 수수료를 제출할 것이고, 이는 Transaction의 빠른 최종성을 보장하게 됩니다. 이러한 게임은 장기적으로 0과 1로 나뉘는 수수료 확률 게임이 될 것입니다.

- <b> WhiteLabel Software Development Kit </b> - Quartz Framework는 Ethereum상의 ERC-20 Token별로 Network를 생성할 수 있으며, 그에 따라서 Whitelabel SDK들을 제공할 수 있습니다. 이 Whitelabel SDK은 각 Mobile OS별로 제공되며, Transaction 수수료를 네트워크에 배포된 Token으로 지불합니다.

## Proof of Stake
기존의 Proof of Stake는 Practical Byzantine Fault Tolerance[[3]](http://pmg.csail.mit.edu/papers/osdi99.pdf)의 구현으로 전체 투표권으로 환산된 담보금의 66.7% 이상에 해당하는 투표를 받는 모델로 구현되어 있습니다. Quartz Framework의 Proof of Stake는 Validator의 극단적인 투표 참여를 독려하기 위해서 전체 투표율에 따라 수수료의 수수 비율을 달리 하는 것으로 Transaction 처리량의 대역폭을 결정하게 됩니다. Validator는 Gossip Protocol로 인해서 Transaction을 동등한 상태로 동기화 하며, 시간이 지남에 따라 이 동등한 상태에 대한 완결성은 상승하게 됩니다.

<p align="center">
  <img src="src/004.png">
  <br>
  <b> Figure 1 </b> - Transaction의 길이는 수수료의 양에 따라 상대적으로 평가됩니다. 수수료가 상대적으로 많으면 높은 길이를, 상대적으로 적으면 낮은 길이를 가집니다.
</p>

동기화된 Mempool은 위와 같이 상대적인 수수료에 기반하여 수수료가 높은 Transaction은 0에 가깝고, 낮은 Transaction은 1에 가깝게 평가됩니다. Transaction 처리 대역폭은 투표에 의해 결정되는데, 예를 들어 70%에 달하는 투표가 이뤄졌다면, 다음과 같은 대역폭이 결정됩니다.

<p align="center">
  <img src="src/005.png">
  <br>
  <b> Figure 2 </b> - Validator의 투표에 따라 처리 될 Transaction을 선별하게 된다.
</p>

100% 투표가 이뤄지게 된다면, 현재의 Block 시간 이전에 생성된 올바른 Transaction은 모두 성공처리가 됩니다. 모든 Node는 이 투표에 대한 증거를 토대로, 자율적으로 Transaction을 검증하게 됩니다.

### Prepare

Quartz의 모든 Node는 현재 시간에 대한 Key Block을 생성할 수 있습니다. 이는 일종의 Bitcoin-NG의 Key Block[[2]](https://www.usenix.org/system/files/conference/nsdi16/nsdi16-paper-eyal.pdf)과 같은 역할을 하는데, 다른 점은 선출과정을 거치지 않고 시간에 대한 증거로써 Key Block을 생성할 수 있다는 점입니다.

```JavaScript
// KeyBlockId = keccak256(KeyBlockIdField);
const KeyBlockIdField = {
  // Genesis 이후 Block Interval*N 에 따른 시작 Unix Time
  StartTime: uint64(UnixTime),
  // Block Interval 이후의 Unix Time
  EndTime: uint64(UnixTime),
  // Network Id에 종속된 KeyBlockId 생성 유도
  NetworkId: string(Hash),
  // 이전 Block에 대한 Id를 참조로 가짐
  PrevBlockId: string(Hash)
}
```

이러한 KeyBlockId는 Validator가 현재 시간대의 투표 증거로 사용할 수 있으며, Node가 Transaction을 발생 시킬 때, 특정 Block을 기점으로 작동할 수 있도록 Trigger 역할을 수행합니다. 이러한 Key Block에는 Transaction이 담겨있지 않으며, 단순 증거로 사용됩니다.

### Vote

Validator는 Quartz의 System Contract에 Token을 예치하는 것으로 될 수 있습니다. 이 System Contract는 Ethereum 상에서 배포되며 배포된 Contract의 ID는 NetworkId 가 되며, Smart Contract에 기록된 시간은 Quartz 기반 Network의 Genesis KeyBlockId가 됩니다.

Validator는 다음과 같은 증거로 해당 시간대에 투표하게 됩니다.

```JavaScript
// VoteId = keccak256(VoteField);
const VoteField = {
  // 목표가 되는 시간대의 Key Block Id
  KeyBlockID: string(Hash),
  // 어떤 공개키로 부터 해당 투표가 발생되었는지
  From: string(Hash),
  // 공개키에 대입되는 비밀키 서명
  Sig: string(Hash)
}
```

Validator는 위에서 보는 Vote를 모든 Node로 전송합니다. Node는 해당 투표를 서명 값으로 검증합니다. 이는 Transaction 처리 대역폭을 결정하는 중요한 역할을 하게 되며, Validator가 미래의 Key Block Id에 미리 투표할 수 없습니다.


### Block Time

Block Interval은 기본 2초로 지정되어 있습니다. Epoch은 Block Interval의 3배로 지정되어 있는데, 이 시간동안에 다음과 같은 일이 일어납니다.

*첫 번째 Epoch*에는 Validator가 투표를 진행하며, 모든 Node는 이를 전송받습니다. *두 번째 Epoch*에는 이를 취합하여 Transaction 처리 대역폭을 결정하고, 대역폭 내에 포함되는 Transaction들을 검증합니다. *세 번째 Epoch*에는 검증된 Transaction을 다음 처럼 Block을 구성하여 공개하도록 합니다.

```JavaScript
// BlockId = keccak256(BlockField);
const BlockField = {
  // 목표가 되는 시간대의 Key Block Id
  KeyBlockID: string(Hash),
  // 해당 Block에 포함된 Merkle Root
  MerkleRoot: string(Hash),
  // 검증된 Transaction의 모음
  Transactions: [...Transaction],
  // Vote's
  Votes: [...Vote]
}
```

다만 이 단계에서 모든 Validator는 동일한 Block을 생성할 수 없을 것입니다. Validator는 검증의 책임만을 가지고

 따라서 다음 조건에 의해서 올바른 Block을 걸러냅니다.

* 모든 Node는 전송받은 Vote 증거를 가진다.
  * Node가 Block에 담겨있는 Vote보다 적게 가진 경우, Block에 있는 Vote를 참조하고 해당 Block을 취한다.
  * Node가 Block에 담겨있는 Vote보다 많이 가진 경우, 해당 Block을 버린다.
  * Node가 Block에 담겨있는 Vote와 동일하게 가진 경우, 해당 Block을 취한다.
  * Validator는 첫 Epoch에서 Vote 증거를 제출했어야 했다.
* 가장 낮은 Transaction Fee는 0이며, 가장 높은 Transaction Fee는 전송받은 Block의 Transaction 들 중 첫 번째에 위치해 있다.
  * 0과 가장 높은 Transaction Fee를 백분율화 하여 0과 1로 나눈다.
  * Vote 증거에 의해서 Transaction 처리 비율을 검증한다. 처리 비율이 맞지 않는 Block은 버린다.
  * 처리 비율에 따른 Transaction들을 검증한다.
  * 위의 과정을 거쳐 올바른 Block이라면 취한다.

### Next Block

이런 방식으로 모든 Node는 Block의 검증과정에 참여하게 되고, 이는 투표 증거에 의해서 모든 Node가 자율적으로 따릅니다. 이 과정에서 성능이 떨어지는 Node는 네트워크 증거를 처리하는데 있어서 지연을 겪을 것이고, 네트워크에서 탈락하게 될 것입니다. 궁극적으로 Block의 합의 비용은 낮추고, Transaction 처리 속도를 상승시킨다고 볼 수 있습니다.

다만 일부 많은 Token Holder가 일부러 투표하지 않고, 높은 수수료만 취한다고 볼 수 있으나 수수료 보상은 투표자들에게만 주어지고, 일부러 많은 Token을 가지고 있다고 하더라도 투표를 하는 것이 자신의 이익에 도움이 되므로 실제로 이러한 일은 일어나지 않을 것으로 보입니다.[[7]](https://bitcoin.org/bitcoin.pdf)

또한 시간의 증거에 의해서 Block이 생성되며, Block이 확정되기 위해서는 Transaction을 필요로 하므로, Transaction이 발생되지 않는 시간에는 Block이 생성되지 않습니다.


### Pseudo Random Number

기초적으로 Validator의 투표 따라서 엔트로피의 증가점이 변경된다고 볼 수 있습니다. 투표량에 따라서 Merkle Patricia Tree[[5]](https://github.com/ethereum/wiki/wiki/Patricia-Tree)의 Root는 예상 불가능하게 변경되며 이는 256bit의 숫자로 이뤄져 난수로 사용이 가능합니다.


## Sharding

Quartz Framework는 EVM상의 배포된 Smart Contract가 내부적으로 상태를 변경하는데 있어 Merkle Patricia Tree[[5]](https://github.com/ethereum/wiki/wiki/Patricia-Tree)를 구성할 수 있도록 합니다. Merkle Tree를 가질 때, Validator의 투표에 따라 변동적인 Transaction 수용량을 가지기 때문에, Smart Contract별로 Merkle Patricia Tree를 가지도록 합니다. 모든 네트워크 이용자는 관찰하고자 하는 특정 Smart Contract의 상태나, 특정한 주소의 잔고 상태를 빠르게 추적할 수 있습니다. 따라서 Node가 State Trie의 특정 주소만을 동기화 하는 것도 가능합니다.


## Crypto Economy & Whitelabel SDK

모든 최종 사용자들은 개인키와 공개키를 관리하지 않아야하고, Transaction 수수료를 지불하기 위해서 Coin을 소지하지 않아야 합니다. 다만 네트워크 이용료로, 네트워크에 배포된 Token을 수수료로 지불하여야 합니다. Token을 수수료로 지불하는 것은 서비스를 이용하고, 네트워크를 유지하기 위한 당연한 행동이 됩니다.

이용자들은 일정한 수수료를 지불하여 서비스를 이용합니다. Validator들은 최대한의 투표를 통해서 수수료를 얻을 것이기 때문에, Transaction이 아주 소량의 수수료를 가지더라도 처리될 것입니다.

이러한 점은 네트워크를 유지하는 보상을 자체적인 자산으로 지불하도록 하여, 가치가 별도의 네트워크를 통해서 창출될 수 있다는 점입니다. 상대적으로 사용성이 떨어지거나, 인기가 없는 네트워크는 자연적으로 도태되어 사라지게 될 것입니다.

또한 최종 사용자가 사용하게 될 지갑이나, DApp은 Whitelabel SDK에 의해 기본적인 작동을 모두 처리할 수 있도록 하여 개발자는 로직과 디자인에 신경쓸 수 있도록 할 것입니다.

## Citations
- [[1]](https://github.com/ethereum/wiki/wiki/White-Paper) "Ethereum White Paper" https://github.com/ethereum/wiki/wiki/White-Paper
- [[2]](https://www.usenix.org/system/files/conference/nsdi16/nsdi16-paper-eyal.pdf) "Bitcoin-NG: A Scalable Blockchain Protocol" https://www.usenix.org/system/files/conference/nsdi16/nsdi16-paper-eyal.pdf
- [[3]](http://pmg.csail.mit.edu/papers/osdi99.pdf) "Practical Byzantine Fault Tolerance" http://pmg.csail.mit.edu/papers/osdi99.pdf
- [[4]](https://dl.acm.org/citation.cfm?doid=41840.41841) "Epidemic algorithms for replicated database maintenance" https://dl.acm.org/citation.cfm?doid=41840.41841
- [[5]](https://github.com/ethereum/wiki/wiki/Patricia-Tree) "Patricia Tree" https://github.com/ethereum/wiki/wiki/Patricia-Tree
- [[6]](https://eprint.iacr.org/2013/881.pdf) "Secure High-Rate Transaction Processing in Bitcoin" https://eprint.iacr.org/2013/881.pdf
- [[7]](https://bitcoin.org/bitcoin.pdf) "Bitcoin: A Peer-to-Peer Electronic Cash System" https://bitcoin.org/bitcoin.pdf
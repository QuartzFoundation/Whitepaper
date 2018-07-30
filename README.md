<h1 align="center">Quartz Framework</h1>
<h2 align="center">A Framework for Blockchain Scalability</h2>
<p align="center">
author <a href="https://ysnim.ink">Yoonsung Choi</a>
</p>
<span align="center">
[![GitHub version](https://badge.fury.io/gh/QuartzWorld%2FWhitepaper.svg)](https://badge.fury.io/gh/QuartzWorld%2FWhitepaper)
</span>

## Abstract

이 문서는 Blockchain의 초당 Transaction 처리 속도를 극도로 끌어올리며, 경제적인 모델을 도입하여 합리적인 수수료를 지불할 수 있는 Quartz Framework라고 불리는 프로토콜 집합체를 설명하고 있습니다. 이 Framework의 핵심은 투표에 따라 Transaction 처리량이 변동되며 따라서 Validator들이 받게 되는 수수료를 달리 하는 것으로 자율적으로 작동하게 됩니다.

이 Framework는 Ethereum과 통합되어 Smart Contract의 작동을 병렬적으로 처리하며, Quartz Framework를 통해 파생되는 Network들은 개별적인 Cryptoeconomy를 확립하게 됩니다.


## Background

Blockchain Network는 Block의 용량적 제한 그리고 처리 단위에 대한 제한으로, 전 세계에서 동시 다발 적으로 발생하는 Transaction을 다수 처리할 수 없으며, 그 마저도 Transaction에 포함된 수수료가 높은 순서대로 처리됩니다.

이러한 상황에서 Transaction 처리 비율을 높이기 위해 GHOST Protocol이 도입되지만, 현재의 Proof of Work Consensus 상에서 Transaction을 처리하기 위한 커다란 요인이 되지 못합니다.

Blockchain은 기본적으로 많은 이용자들의 공용 플랫폼입니다. Initial Coin Offering 과 같은 이벤트는 Transaction 수수료가 자연스럽게 상승하게 되는 주 요인이며, 이러한 이벤트에 참여하지 않는 다수의 이용자들은 갑작스럽게 상승한 Transaction 수수료를 따라야 합니다.

Smart Contract의 발전으로 다양한 Token이 Blockchain 상에서 발행 되었으며, Token들은 이용 방법과 가치가 각각 다릅니다. 하지만 이러한 Token을 전송하거나 이용할 때는 주 Blockchain이 제공하는 Coin을 이용하여 Transaction 수수료를 지불하여야 하는 단점이 존재합니다.

이러한 문제들은 최근까지도 지속적으로 이뤄지고 있으며, 이 문서에서는 위와 같은 상황들에 대한 해결 방법이 되고자 작성되었습니다.


## Introduction

Ethereum과 Bitcoin을 비롯하여 Blockchain은 상태를 저장하고, 변경의 기록을 Block에 담아 모든 Peer to Peer 네트워크를 통해 참여자들이 동일하게 가지게 됩니다. 또한 Smart Contract의 발전으로 Blockchain의 상태 변경을 프로그램 할 수 있게 되었고, 이를 통해서 중재자 없는 다양한 서비스들이 세상에 나올 수 있게 되었습니다.

하지만 이 모든 서비스들의 Transaction을 처리하기에는 Blockchain이 수용할 수 있는 초당 Transaction 수가 너무 낮다는 것이 문제입니다. 이러한 Blockchain의 Scalability를 On-chain에서 처리하는 것은 너무 많은 대기 시간을 요구합니다.

보통 Block 보상으로 주어지는 암호화폐를 Coin, Blockchain을 기반으로 만들어진 암호화폐를 Token이라 부르는데, 또한 Decentralized Application(이하 DApp)을 작동 시키기 위해서 Transaction 수수료로 Coin을 사용하게 됩니다.

Network 또는 DApp의 가치는 실질적으로 사용하는 사람들에 의해 결정됩니다. 수수료 보다 낮은 가치를 지닌 Token을 전송하고 사용하는 경우에는 어떨까요? 많은 기능적 이익을 제공하지만, 수수료로 더욱 많은 비용을 지불한다면 가치가 보장되기 어려운 환경이 될 것입니다.

예를 들어 Augur나 Aragon과 같은 DApp은 Ether를 수수료로 지불하여 Token을 사용하도록 하는데, 이는 필수적으로 Ether를 필요로 한다는 문제가 있습니다. 때문에 Transaction은 On-chain이 아닌 Off-chain에서 처리되어야 합니다. 하지만 Off-chain은 State가 저장되지 않고, 암호작업에 많은 리소스를 투입하는 것으로 상태를 유지합니다.

결국이는 다음과 같은 극단으로 나뉘게 됩니다.

* Blockchain을 통해서 전체 State를 간단히 추적하는 방법
* 많은 암호 작업을 통해서 나와 연결된 State의 추적하는 방법

Quartz Framework를 생성된 Network는 기본적으로 Ethereum에 연결되어 있지만, Off-chain으로 작동합니다. 이 네트워크는 각각의 Token 또는 Wrapped Ether(이하 WETH)를 통해서 자율적인 경제 체계를 가지고, 많은 수의 Transaction을 수용할 수 있게 됩니다.

다음과 같은 사용 사례들이 존재할 수 있습니다.

* 법정화폐를 기반으로 하는 Point of Sales System Network
* DApp을 위한 Network Pool
* Multi-Party Computation
* 소상공인을 위한 Point 시스템, 또는 지급 결제
* Ticketing / Ticket Trade Platform
* Private Network



## Quartz Framework

Blockchain의 확장성 문제는 다음과 같은 방법으로 해결할 수 있습니다.


### Protocol을 통한 개선

Blockchain의 Block은 크기가 제한되어 있습니다. Bitcoin의 경우 Transaction이 담겨질 공간에 대한 용량적 제한이 있고, Ethereum의 경우 실행 단위에 대해 Gas 제한을 두어 Block 크기가 제한되어 있습니다. Ethereum의 경우 Gas 제한을 채굴자가 설정할 수 있으나, Block 보상으로 인해 수수료를 위한 Block 크기에 대한 경쟁을 하지 않고 있습니다. 단순히 Block의 크기가 증가하면, Block에 담겨지는 Transaction의 수는 증가할 것이고, 결과적으로 초당 처리할 수 있는 Transaction 수가 증가하게 됩니다.

기존의 Blockchain의 경우 같은 번호를 가진 Block이 2개 이상 생성된 경우, 앞으로 생성될 Block의 길이에 의해 자연스럽게 나머지 Block이 도태되어 버려지게 됩니다. 이때 도태되는 Block을 Orphan Block이라 부릅니다.

GHOST Protocol은 Orphan Block에 들어있는 Transaction이 올바르게 처리된 것일 때, 기존 Block과 합치는 것을 말합니다. 실질적으로 같은 번호의 Block이 담게되는 Transaction은 더욱 많아지게 됩니다. GHOST Protocol은 Block Interval이 짧은 Blockchain의 보안을 더욱 상승시키기 위해서 제안되었으나, Transaction을 더욱 많이 수용하기 위한 방법으로도 사용되고 있습니다.

또 다른 대표적인 방법으로, Proof of Work Consensus를 Proof of Stake Consensus로 변경하는 방법이 있습니다.

Proof of Work는 Transaction을 처리하는 시간보다, Block을 생성하는 시간에 더욱 많은 연산력을 사용합니다. 그렇기 때문에 Block을 생성하는 시간보다 Transaction을 검증하는데 연산력을 사용할 수 있도록 지분을 기반으로 하는 Proof of Stake로 합의 알고리즘을 변경한다면 더욱 많은 Transaction을 수용할 수 있게 됩니다.


### 검증 연산을 줄이는 방법

이는 각각 On-chain과 Off-chain으로 나뉠 수 있으며, 실질적으로 연구되고 있는 것은 Zero Knowledge Proof, Sharding입니다.

대체로 Blockchain은 암호학적 연산을 수행하는데 많은 연산력을 필요로 하는데 이는 입력과 출력이 동일하다는 간단한 연산을 통해 검증 비용 및 크기를 줄일 수 있다는 것이 특징입니다.

Zero Knowledge Proof는 zkSNARKs와 zkSTARKs, Bullet Proof와 같은 것들이 존재하며, 이는 입력과 출력을 동일하게 하다는 수학적 보장으로 상세한 전송 State를 숨기는 방법입니다.

Sharding은 Ethereum의 경우 모든 상태를 Merkle Patricia Tree를 이용하여 저장합니다. 여기에서 각 Shard는 Tree의 하위 부분에 대한 검증을 하는 대신 주 Chain에는 결과만 전송하는 것으로, 이 또한 검증 비용의 크기를 획기적으로 줄이게 됩니다.


### 2-Layer Solution

Plasma의 경우 또한 동일합니다. Transaction의 내용을 Rootchain에 전송하지 않고, Transaction ID 만 전송하고, 주기적인 검증을 통해 Transaction이 올바른지 검증하게 됩니다.


### Inter-Blockchain

이는 Blockchain과 연결되는 Blockchain을 말합니다. 이는 주 Blockchain의 Transaction들을 연결된 Blockchain에서 처리한 다음에, 결과만 주 Blockchain에 공개되는 것을 말합니다.

주 Blockchain에 연결되는 Inter-Blockchain은 



# 複数拠点接続プロジェクト

## プロジェクト概要
全国に3拠点（本社、支社、データセンター）を持つ企業のネットワーク接続を設計・構築するプロジェクトです。このプロジェクトでは、ルーティングプロトコル（OSPF、EIGRP）を活用して、拠点間の効率的で冗長性のある接続を実現します。また、IPアドレス設計、サブネット化、ルートの集約など、IPコネクティビティに関する重要な技術を実践します。

## ビジネス要件

### クライアント情報
- **会社名**: テクノソリューション株式会社
- **業種**: ITサービス
- **拠点情報**:
  - 本社（東京）: 従業員150名
  - 支社（大阪）: 従業員50名
  - データセンター（埼玉）: サーバー環境、管理者5名

### 要件
1. 3拠点間の安定した接続
2. 拠点間通信の冗長性確保
3. 効率的なルーティング
4. 将来の拡張性を考慮したIPアドレス設計
5. トラフィック最適化
6. 障害時の迅速な復旧
7. 拠点間通信の監視と管理

## 技術要件

### ネットワーク機器
- **本社**:
  - エッジルーター: Cisco 4331シリーズ x2
  - コアスイッチ: Cisco Catalyst 3850シリーズ x2
- **支社**:
  - エッジルーター: Cisco 4321シリーズ x2
  - コアスイッチ: Cisco Catalyst 3650シリーズ x1
- **データセンター**:
  - エッジルーター: Cisco 4351シリーズ x2
  - コアスイッチ: Cisco Nexus 9300シリーズ x2

### ネットワーク設計
- **WAN接続**:
  - 本社-支社: 専用線（100Mbps）+ バックアップ回線（50Mbps）
  - 本社-データセンター: 専用線（1Gbps）+ バックアップ回線（500Mbps）
  - 支社-データセンター: 専用線（100Mbps）

- **IPアドレス設計**:
  - 本社: 10.1.0.0/16
    - 社内LAN: 10.1.0.0/17
    - 管理ネットワーク: 10.1.128.0/24
    - DMZ: 10.1.129.0/24
    - WAN接続: 10.1.254.0/24
  - 支社: 10.2.0.0/16
    - 社内LAN: 10.2.0.0/17
    - 管理ネットワーク: 10.2.128.0/24
    - WAN接続: 10.2.254.0/24
  - データセンター: 10.3.0.0/16
    - サーバーファーム: 10.3.0.0/17
    - 管理ネットワーク: 10.3.128.0/24
    - WAN接続: 10.3.254.0/24

- **ルーティングプロトコル設計**:
  - 内部ルーティング: OSPF
    - エリア0: バックボーン（WAN接続）
    - エリア1: 本社
    - エリア2: 支社
    - エリア3: データセンター
  - ルート集約の実装
  - デフォルトルートの配布

## プロジェクト成果物

### 1. ネットワーク設計図
- [物理トポロジー図](../network_diagrams/03_multi_site_physical.png)
- [論理トポロジー図](../network_diagrams/03_multi_site_logical.png)
- [IPアドレス設計図](./design/ip_addressing_scheme.png)
- [OSPFエリア設計図](./design/ospf_areas.png)

### 2. 機器設定
- **本社**:
  - [エッジルーター設定](./configs/hq_edge_router_config.txt)
  - [コアスイッチ設定](./configs/hq_core_switch_config.txt)
- **支社**:
  - [エッジルーター設定](./configs/branch_edge_router_config.txt)
  - [コアスイッチ設定](./configs/branch_core_switch_config.txt)
- **データセンター**:
  - [エッジルーター設定](./configs/dc_edge_router_config.txt)
  - [コアスイッチ設定](./configs/dc_core_switch_config.txt)

### 3. 実装手順
- [IPアドレス設計と割り当て手順](./implementation/ip_addressing_implementation.md)
- [OSPF基本設定手順](./implementation/ospf_basic_setup.md)
- [OSPFエリア設定手順](./implementation/ospf_area_setup.md)
- [ルート集約設定手順](./implementation/route_summarization.md)
- [冗長パス設定手順](./implementation/redundant_paths.md)
- [デフォルトルート配布手順](./implementation/default_route_distribution.md)

### 4. 検証結果
- [拠点間接続性テスト結果](./verification/inter_site_connectivity.md)
- [OSPF隣接関係検証](./verification/ospf_adjacency.md)
- [ルーティングテーブル検証](./verification/routing_table.md)
- [フェイルオーバーテスト結果](./verification/failover_test.md)
- [帯域幅とレイテンシテスト結果](./verification/bandwidth_latency_test.md)

### 5. トラブルシューティング事例
- [OSPF隣接関係問題の解決](./troubleshooting/ospf_adjacency_issues.md)
- [ルート再配布問題の解決](./troubleshooting/route_redistribution_issues.md)
- [WAN接続障害の対応](./troubleshooting/wan_connectivity_issues.md)
- [サブネット設計ミスの修正](./troubleshooting/subnet_design_correction.md)

## 実装のポイント

### 1. IPアドレス設計のポイント
- 階層的なアドレス設計による管理性の向上
- 将来の拡張を考慮したサブネットサイズの決定
- 効率的なルート集約のためのアドレス割り当て
- 一貫性のあるアドレス設計方針

### 2. OSPFルーティング設計のポイント
- 適切なエリア分割によるルーティングテーブルの最適化
- エリア間のトラフィックフローの考慮
- バックボーンエリア（エリア0）の適切な設計
- ルート集約によるルーティングテーブルサイズの削減

### 3. 冗長性設計のポイント
- 複数のWAN接続による冗長性確保
- 等コストパスによるロードバランシング
- 非等コストパスでのバックアップ経路設定
- 障害検出と迅速な経路切り替え

### 4. パフォーマンス最適化のポイント
- 最適なパスの選択（コスト設定）
- 帯域幅に基づいたコスト計算
- ルート集約によるルーティングアップデートの最適化
- 効率的なトラフィックエンジニアリング

## 学んだこと
- 複数拠点ネットワークにおけるルーティング設計の重要性
- OSPFエリア設計による大規模ネットワークの効率的な管理
- IPアドレス設計が将来の拡張性と管理性に与える影響
- 冗長性と最適なパス選択のバランス
- 実際のネットワーク環境でのトラブルシューティング手法

## 次のステップ
- BGPの導入によるインターネット接続の冗長化
- MPLS VPNサービスへの移行検討
- IPv6アドレス設計と移行計画
- SD-WANソリューションの評価
- ネットワークパフォーマンスモニタリングの強化

## 参考リソース
- [OSPF Design Guide](https://www.cisco.com/c/en/us/support/docs/ip/open-shortest-path-first-ospf/7039-1.html) - Cisco公式ドキュメント
- [IP Addressing: IPv4 Addressing Configuration Guide](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/ipaddr_ipv4/configuration/15-mt/ipv4-15-mt-book.html) - Cisco公式ガイド
- [Routing TCP/IP, Volume 1](https://www.ciscopress.com/store/routing-tcp-ip-volume-1-9781587052026) by Jeff Doyle & Jennifer DeHaven Carroll
- [CCNA 200-301 Official Cert Guide, Volume 1](https://www.ciscopress.com/store/ccna-200-301-official-cert-guide-volume-1-9780135792735) by Wendell Odom
- [Optimal Routing Design](https://www.ciscopress.com/store/optimal-routing-design-9781587142246) by Russ White, Alvaro Retana & Don Slice
- [Cisco Live: Advanced OSPF Deployment Considerations](https://www.ciscolive.com/c/dam/r/ciscolive/us/docs/2018/pdf/BRKRST-3310.pdf) - Cisco Liveセッション資料
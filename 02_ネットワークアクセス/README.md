# 企業VLAN環境構築プロジェクト

## プロジェクト概要
中規模企業（従業員100名程度）の本社オフィス向けに、部門別VLANを使用した効率的で安全なネットワーク環境を設計・構築するプロジェクトです。このプロジェクトでは、スイッチング技術、VLAN、トランキング、スパニングツリープロトコル、EtherChannelなどの技術を活用して、セグメント化されたネットワークインフラを実装します。

## ビジネス要件

### クライアント情報
- **会社名**: グローバルトレード株式会社
- **業種**: 貿易・商社
- **従業員数**: 100名
- **部門構成**: 営業部（30名）、管理部（20名）、経理部（15名）、IT部（10名）、役員（5名）、共有エリア（20名収容）
- **オフィス**: 2フロア（各約400㎡）

### 要件
1. 部門ごとのネットワークセグメント化
2. 部門間の適切なアクセス制御
3. ネットワークの可用性と冗長性の確保
4. 効率的なネットワークリソースの利用
5. 将来の拡張性を考慮した設計
6. 音声通信（IP電話）のサポート
7. 会議室用の無線LANアクセス

## 技術要件

### ネットワーク機器
- コアスイッチ: Cisco Catalyst 3650シリーズ x2
- アクセススイッチ: Cisco Catalyst 2960シリーズ x6
- 無線LANアクセスポイント: Cisco Aironet x4
- L3ルーター: Cisco 4321シリーズ x1

### ネットワーク設計
- **VLAN設計**:
  - VLAN 10: 営業部（192.168.10.0/24）
  - VLAN 20: 管理部（192.168.20.0/24）
  - VLAN 30: 経理部（192.168.30.0/24）
  - VLAN 40: IT部（192.168.40.0/24）
  - VLAN 50: 役員（192.168.50.0/24）
  - VLAN 60: 共有エリア（192.168.60.0/24）
  - VLAN 70: 音声VLAN（192.168.70.0/24）
  - VLAN 80: 管理VLAN（192.168.80.0/24）
  - VLAN 99: ネイティブVLAN

- **スパニングツリー設計**:
  - RPVST+（Rapid Per-VLAN Spanning Tree Plus）
  - コアスイッチをルートブリッジに設定
  - バックアップルートブリッジの設定
  - PortFastとBPDUガードの設定

- **EtherChannel設計**:
  - コアスイッチ間: 4ポートEtherChannel（LACP）
  - コアスイッチとアクセススイッチ間: 2ポートEtherChannel（LACP）

## プロジェクト成果物

### 1. ネットワーク設計図
- [物理トポロジー図](../network_diagrams/02_vlan_physical.png)
- [論理トポロジー図](../network_diagrams/02_vlan_logical.png)
- [VLAN設計図](./design/vlan_design.png)
- [スパニングツリー設計図](./design/stp_design.png)

### 2. 機器設定
- [コアスイッチ設定](./configs/core_switch_config.txt)
- [アクセススイッチ設定](./configs/access_switch_config.txt)
- [L3ルーター設定](./configs/router_config.txt)
- [EtherChannel設定](./configs/etherchannel_config.txt)
- [スパニングツリー設定](./configs/stp_config.txt)

### 3. 実装手順
- [スイッチ初期設定手順](./implementation/switch_initial_setup.md)
- [VLAN設定手順](./implementation/vlan_setup.md)
- [トランキング設定手順](./implementation/trunking_setup.md)
- [スパニングツリー設定手順](./implementation/stp_setup.md)
- [EtherChannel設定手順](./implementation/etherchannel_setup.md)
- [VLAN間ルーティング設定手順](./implementation/inter_vlan_routing.md)
- [音声VLAN設定手順](./implementation/voice_vlan_setup.md)

### 4. 検証結果
- [VLAN接続性テスト結果](./verification/vlan_connectivity_test.md)
- [スパニングツリー動作検証](./verification/stp_verification.md)
- [EtherChannel動作検証](./verification/etherchannel_verification.md)
- [フェイルオーバーテスト結果](./verification/failover_test.md)
- [帯域幅テスト結果](./verification/bandwidth_test.md)

### 5. トラブルシューティング事例
- [VLAN間通信問題の解決](./troubleshooting/inter_vlan_communication.md)
- [スパニングツリーループの検出と解決](./troubleshooting/stp_loop.md)
- [EtherChannelの不一致問題の解決](./troubleshooting/etherchannel_mismatch.md)
- [トランクポート設定ミスの修正](./troubleshooting/trunk_misconfiguration.md)

## 実装のポイント

### 1. VLAN設計のポイント
- 部門の役割と通信要件に基づいたVLAN分割
- 適切なIPアドレス設計（将来の拡張を考慮）
- 管理VLANの分離によるセキュリティ向上
- 音声VLANの適切な設定（QoS考慮）

### 2. スパニングツリー設計のポイント
- ネットワークトポロジーに最適なルートブリッジの配置
- 冗長パスの効率的な管理
- PortFastとBPDUガードによるエッジポートの保護
- RPVST+の利点を活かした設計

### 3. EtherChannel設計のポイント
- 適切なリンク集約によるスループット向上
- LACPを使用した動的EtherChannel構成
- ロードバランシング方式の最適化
- リンク障害時の冗長性確保

### 4. セキュリティ設計のポイント
- 未使用ポートのシャットダウン
- ポートセキュリティの実装
- DHCP Snoopingの設定
- 管理アクセスの制限

## 学んだこと
- 企業ネットワークにおけるVLAN設計の重要性
- スパニングツリープロトコルによるループ防止の実践
- EtherChannelによる帯域幅と冗長性の向上
- 論理的なネットワークセグメンテーションの利点
- 適切なドキュメント作成の重要性

## 次のステップ
- セキュリティ強化（802.1X認証の導入）
- SDN（Software-Defined Networking）の検討
- ネットワーク監視システムの導入
- IPv6への移行計画

## 参考リソース
- [Cisco Campus Network for High Availability Design Guide](https://www.cisco.com/c/en/us/td/docs/solutions/Enterprise/Campus/HA_campus_DG/hacampusdg.html)
- [Cisco LAN Switching Configuration Handbook](https://www.ciscopress.com/store/cisco-lan-switching-configuration-handbook-9781587141096)
- [Understanding and Configuring Spanning Tree Protocol (STP) on Catalyst Switches](https://www.cisco.com/c/en/us/support/docs/lan-switching/spanning-tree-protocol/5234-5.html)
- [Cisco EtherChannel - Configuration Examples and TechNotes](https://www.cisco.com/c/en/us/support/docs/lan-switching/etherchannel/98469-ios-etherchannel.html)
- [CCNA 200-301 Official Cert Guide, Volume 1](https://www.ciscopress.com/store/ccna-200-301-official-cert-guide-volume-1-9780135792735) by Wendell Odom
- [Network Warrior: Everything You Need to Know That Wasn't on the CCNA Exam](https://www.oreilly.com/library/view/network-warrior-2nd/9781449307974/) by Gary A. Donahue
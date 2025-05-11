# 実践ラボと検証環境

## 概要
このディレクトリには、各プロジェクトで実施した実践的なラボ環境の構成、検証手順、テスト結果が含まれています。これらのラボは、設計した内容を実際に検証し、実装前に問題点を発見・解決するために実施しています。また、新しい技術やコンセプトを学習・検証するための環境としても活用しています。

## ラボ環境

### 仮想ラボ環境
- **Cisco Packet Tracer**
  - バージョン: 8.2.0
  - 用途: 基本的なネットワーク構成の検証、初期プロトタイピング
  - 特徴: 軽量で迅速にラボを構築可能、基本的なCisco機能をサポート

- **GNS3**
  - バージョン: 2.2.33
  - 用途: より高度なネットワーク構成の検証、実機に近い環境でのテスト
  - 特徴: 実際のIOSイメージを使用、より現実的なシミュレーション

- **EVE-NG**
  - バージョン: 3.0 Community Edition
  - 用途: 複雑なマルチベンダー環境の検証、大規模ネットワークのシミュレーション
  - 特徴: 多様なネットワーク機器をサポート、Webベースのアクセス

### 物理ラボ環境
- **Cisco機器**
  - Cisco 2901 ISRルーター x2
  - Cisco Catalyst 2960スイッチ x4
  - Cisco ASA 5505ファイアウォール x1
  - Cisco Aironet 1142アクセスポイント x2

- **サーバー環境**
  - VMware ESXi 7.0ホスト
  - Ubuntu Server 20.04 LTS VM (自動化サーバー)
  - Windows Server 2019 VM (Active Directory, DHCP, DNS)
  - CentOS 8 VM (監視サーバー)

## プロジェクト別ラボ構成

### 01 - 小規模オフィスネットワーク構築プロジェクト

#### ラボ環境構成
- [小規模オフィスラボトポロジー](./01_small_office/topology.png)
- [機器リスト](./01_small_office/equipment_list.md)
- [IPアドレス割り当て表](./01_small_office/ip_addressing.md)

#### 検証シナリオ
1. [基本接続性テスト](./01_small_office/tests/connectivity_test.md)
2. [DHCPサービス検証](./01_small_office/tests/dhcp_test.md)
3. [インターネット接続検証](./01_small_office/tests/internet_test.md)
4. [無線LAN接続検証](./01_small_office/tests/wireless_test.md)
5. [障害シミュレーションテスト](./01_small_office/tests/failure_test.md)

#### 設定ファイル
- [ルーター設定](./01_small_office/configs/router.txt)
- [スイッチ設定](./01_small_office/configs/switch.txt)
- [ファイアウォール設定](./01_small_office/configs/firewall.txt)
- [無線LANコントローラ設定](./01_small_office/configs/wlc.txt)

#### 検証結果
- [テスト結果サマリー](./01_small_office/results/test_summary.md)
- [パフォーマンス測定結果](./01_small_office/results/performance.md)
- [問題点と解決策](./01_small_office/results/issues_solutions.md)

### 02 - 企業VLAN環境構築プロジェクト

#### ラボ環境構成
- [企業VLAN環境ラボトポロジー](./02_vlan_environment/topology.png)
- [機器リスト](./02_vlan_environment/equipment_list.md)
- [VLAN設計表](./02_vlan_environment/vlan_design.md)

#### 検証シナリオ
1. [VLAN接続性テスト](./02_vlan_environment/tests/vlan_connectivity.md)
2. [トランキング検証](./02_vlan_environment/tests/trunking_test.md)
3. [スパニングツリー検証](./02_vlan_environment/tests/stp_test.md)
4. [EtherChannel検証](./02_vlan_environment/tests/etherchannel_test.md)
5. [VLAN間ルーティング検証](./02_vlan_environment/tests/inter_vlan_routing.md)
6. [障害シミュレーションテスト](./02_vlan_environment/tests/failure_test.md)

#### 設定ファイル
- [コアスイッチ設定](./02_vlan_environment/configs/core_switch.txt)
- [アクセススイッチ設定](./02_vlan_environment/configs/access_switch.txt)
- [L3ルーター設定](./02_vlan_environment/configs/router.txt)

#### 検証結果
- [テスト結果サマリー](./02_vlan_environment/results/test_summary.md)
- [スパニングツリー収束時間測定](./02_vlan_environment/results/stp_convergence.md)
- [EtherChannelパフォーマンス測定](./02_vlan_environment/results/etherchannel_performance.md)
- [問題点と解決策](./02_vlan_environment/results/issues_solutions.md)

### 03 - 複数拠点接続プロジェクト

#### ラボ環境構成
- [複数拠点ラボトポロジー](./03_multi_site/topology.png)
- [機器リスト](./03_multi_site/equipment_list.md)
- [IPアドレス設計表](./03_multi_site/ip_addressing.md)
- [OSPFエリア設計](./03_multi_site/ospf_areas.md)

#### 検証シナリオ
1. [拠点間接続性テスト](./03_multi_site/tests/inter_site_connectivity.md)
2. [OSPF隣接関係検証](./03_multi_site/tests/ospf_adjacency.md)
3. [ルート集約検証](./03_multi_site/tests/route_summarization.md)
4. [WAN障害シミュレーション](./03_multi_site/tests/wan_failure.md)
5. [ルーティングコンバージェンステスト](./03_multi_site/tests/routing_convergence.md)

#### 設定ファイル
- [本社ルーター設定](./03_multi_site/configs/hq_router.txt)
- [支社ルーター設定](./03_multi_site/configs/branch_router.txt)
- [データセンタールーター設定](./03_multi_site/configs/dc_router.txt)

#### 検証結果
- [テスト結果サマリー](./03_multi_site/results/test_summary.md)
- [OSPFコンバージェンス時間測定](./03_multi_site/results/ospf_convergence.md)
- [WAN帯域幅利用率](./03_multi_site/results/wan_bandwidth.md)
- [問題点と解決策](./03_multi_site/results/issues_solutions.md)

### 04 - ネットワークサービス最適化プロジェクト

#### ラボ環境構成
- [ネットワークサービスラボトポロジー](./04_network_services/topology.png)
- [機器リスト](./04_network_services/equipment_list.md)
- [サービス設計表](./04_network_services/services_design.md)

#### 検証シナリオ
1. [DHCPサービス検証](./04_network_services/tests/dhcp_test.md)
2. [NAT/PAT機能検証](./04_network_services/tests/nat_test.md)
3. [NTP同期検証](./04_network_services/tests/ntp_test.md)
4. [QoSパフォーマンス検証](./04_network_services/tests/qos_test.md)
5. [HSRP冗長性検証](./04_network_services/tests/hsrp_test.md)
6. [サービス障害シミュレーション](./04_network_services/tests/service_failure.md)

#### 設定ファイル
- [DHCPサーバー設定](./04_network_services/configs/dhcp_server.txt)
- [NAT/PATルーター設定](./04_network_services/configs/nat_router.txt)
- [NTPサーバー設定](./04_network_services/configs/ntp_server.txt)
- [QoS設定](./04_network_services/configs/qos_config.txt)
- [HSRP設定](./04_network_services/configs/hsrp_config.txt)

#### 検証結果
- [テスト結果サマリー](./04_network_services/results/test_summary.md)
- [QoSパフォーマンス測定](./04_network_services/results/qos_performance.md)
- [HSRPフェイルオーバー時間測定](./04_network_services/results/hsrp_failover.md)
- [問題点と解決策](./04_network_services/results/issues_solutions.md)

### 05 - セキュアネットワーク構築プロジェクト

#### ラボ環境構成
- [セキュリティラボトポロジー](./05_security/topology.png)
- [機器リスト](./05_security/equipment_list.md)
- [セキュリティ設計表](./05_security/security_design.md)

#### 検証シナリオ
1. [ファイアウォールポリシー検証](./05_security/tests/firewall_policy_test.md)
2. [ACL機能検証](./05_security/tests/acl_test.md)
3. [AAA認証検証](./05_security/tests/aaa_test.md)
4. [802.1X認証検証](./05_security/tests/dot1x_test.md)
5. [VPN接続検証](./05_security/tests/vpn_test.md)
6. [侵入検知/防御検証](./05_security/tests/ids_ips_test.md)
7. [セキュリティ侵害シミュレーション](./05_security/tests/security_breach.md)

#### 設定ファイル
- [ファイアウォール設定](./05_security/configs/firewall.txt)
- [ACL設定](./05_security/configs/acl_config.txt)
- [AAAサーバー設定](./05_security/configs/aaa_server.txt)
- [802.1X設定](./05_security/configs/dot1x_config.txt)
- [VPN設定](./05_security/configs/vpn_config.txt)

#### 検証結果
- [テスト結果サマリー](./05_security/results/test_summary.md)
- [セキュリティ監査レポート](./05_security/results/security_audit.md)
- [侵入テスト結果](./05_security/results/penetration_test.md)
- [問題点と解決策](./05_security/results/issues_solutions.md)

### 06 - ネットワーク自動化プロジェクト

#### ラボ環境構成
- [自動化ラボトポロジー](./06_automation/topology.png)
- [機器リスト](./06_automation/equipment_list.md)
- [自動化プラットフォーム構成](./06_automation/platform_setup.md)

#### 検証シナリオ
1. [Pythonスクリプト検証](./06_automation/tests/python_script_test.md)
2. [API統合検証](./06_automation/tests/api_integration_test.md)
3. [Ansibleプレイブック検証](./06_automation/tests/ansible_playbook_test.md)
4. [CI/CDパイプライン検証](./06_automation/tests/cicd_pipeline_test.md)
5. [設定自動化検証](./06_automation/tests/config_automation_test.md)
6. [障害検知と自動復旧検証](./06_automation/tests/auto_remediation_test.md)

#### コードとスクリプト
- [Pythonスクリプト](./06_automation/code/python/)
- [Ansibleプレイブック](./06_automation/code/ansible/)
- [API呼び出しスクリプト](./06_automation/code/api_calls/)
- [CI/CD設定ファイル](./06_automation/code/cicd/)

#### 検証結果
- [テスト結果サマリー](./06_automation/results/test_summary.md)
- [自動化効率測定](./06_automation/results/automation_efficiency.md)
- [エラー処理検証結果](./06_automation/results/error_handling.md)
- [問題点と解決策](./06_automation/results/issues_solutions.md)

## ラボ実施のベストプラクティス

### ラボ環境の準備
1. **明確な目標設定**
   - 検証する機能や設定を明確に定義
   - 成功基準を事前に設定

2. **適切なツールの選択**
   - 検証内容に適したシミュレーションツールを選択
   - 必要に応じて物理機器と仮想環境を組み合わせる

3. **ドキュメント準備**
   - ラボトポロジー図の作成
   - IPアドレス計画の文書化
   - テスト手順書の準備

### テスト実施
1. **段階的なアプローチ**
   - 基本機能から順にテスト
   - 複雑な機能や統合テストは後半で実施

2. **詳細な記録**
   - コマンド出力のキャプチャ
   - 問題発生時の状況記録
   - 設定変更の履歴管理

3. **障害シミュレーション**
   - 様々な障害シナリオをテスト
   - 復旧手順の検証

### 結果分析
1. **期待値との比較**
   - テスト結果と期待値の比較
   - 差異の分析と原因究明

2. **パフォーマンス評価**
   - レイテンシ、スループット、コンバージェンス時間などの測定
   - ベースラインとの比較

3. **改善点の特定**
   - 設計や設定の最適化ポイントの特定
   - 追加テストの必要性の評価

## ラボ環境のセットアップガイド

- [Packet Tracerセットアップガイド](./setup_guides/packet_tracer_setup.md)
- [GNS3セットアップガイド](./setup_guides/gns3_setup.md)
- [EVE-NGセットアップガイド](./setup_guides/eve_ng_setup.md)
- [物理ラボセットアップガイド](./setup_guides/physical_lab_setup.md)
- [自動化環境セットアップガイド](./setup_guides/automation_env_setup.md)

## 参考リソース

- [Cisco DevNet Sandbox](https://developer.cisco.com/site/sandbox/)
- [GNS3 Academy](https://academy.gns3.com/)
- [EVE-NG Community](https://www.eve-ng.net/index.php/community/)
- [Cisco Learning Network Labs](https://learningnetwork.cisco.com/s/learning-labs)
- [David Bombal's YouTube Channel](https://www.youtube.com/c/DavidBombal)
- [Network Lessons](https://networklessons.com/)
- [INE Labs](https://ine.com/)
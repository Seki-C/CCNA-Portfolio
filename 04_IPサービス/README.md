# IPサービス

## 概要
IPサービスは、ネットワークの機能を拡張し、管理性、冗長性、セキュリティを向上させるための様々なプロトコルとテクノロジーを含みます。このセクションでは、DHCP、NAT、NTP、SNMP、QoS、Syslog、FHRPなどのIPサービスについて学びます。

## 学習トピック

### 1. DHCP（Dynamic Host Configuration Protocol）
- **DHCPの概要と機能**
  - IPアドレスの動的割り当て
  - サブネットマスク、デフォルトゲートウェイ、DNSサーバーなどの設定情報の提供
- **DHCPの動作**
  - DORA（Discover, Offer, Request, Acknowledge）プロセス
  - リース期間
  - リース更新
- **DHCPサーバーの設定**
  - スコープの作成
  - 除外アドレス
  - 予約
  - オプション
- **DHCPリレーエージェント**
- **IPv6のDHCP**
  - DHCPv6
  - ステートフル vs ステートレス

### 2. NAT（Network Address Translation）
- **NATの概要と目的**
  - プライベートアドレスとパブリックアドレスの変換
  - IPv4アドレス枯渇問題への対応
  - セキュリティの向上
- **NATの種類**
  - スタティックNAT
  - ダイナミックNAT
  - PAT（Port Address Translation）/NAT Overload
- **NATの設定**
  - 内部ネットワークと外部ネットワークの定義
  - 変換ルールの設定
  - ACLとの連携
- **NATの確認とトラブルシューティング**
- **NAT64（IPv6-IPv4変換）**

### 3. NTP（Network Time Protocol）
- **NTPの概要と重要性**
  - 時刻同期の必要性
  - ログ分析とトラブルシューティングにおける時刻の重要性
- **NTPの階層（Stratum）**
- **NTPの設定**
  - NTPサーバーの設定
  - NTPクライアントの設定
  - 認証の設定
- **NTPの確認とトラブルシューティング**

### 4. SNMP（Simple Network Management Protocol）
- **SNMPの概要と機能**
  - ネットワーク管理
  - 監視
  - 通知
- **SNMPのコンポーネント**
  - マネージャ
  - エージェント
  - MIB（Management Information Base）
  - OID（Object Identifier）
- **SNMPのバージョン**
  - SNMPv1
  - SNMPv2c
  - SNMPv3
- **SNMPの設定**
  - コミュニティストリング
  - トラップ
  - 認証と暗号化（SNMPv3）
- **SNMPの確認とトラブルシューティング**

### 5. QoS（Quality of Service）
- **QoSの概要と必要性**
  - 帯域幅の最適化
  - 遅延、ジッター、パケット損失の管理
  - アプリケーションの優先順位付け
- **QoSモデル**
  - Best-Effort
  - IntServ（Integrated Services）
  - DiffServ（Differentiated Services）
- **QoSの要素**
  - 分類とマーキング
  - 輻輳管理
  - 輻輳回避
  - ポリシングとシェーピング
  - リンク効率化メカニズム
- **QoSの設定**
  - MQC（Modular QoS CLI）
  - クラスマップ
  - ポリシーマップ
  - サービスポリシー
- **QoSの確認とトラブルシューティング**

### 6. Syslog
- **Syslogの概要と機能**
  - システムメッセージのログ記録
  - 中央集中型ログ管理
- **Syslogの重要度レベル（0-7）**
- **Syslogの設定**
  - ローカルログの設定
  - リモートSyslogサーバーの設定
  - タイムスタンプの設定
- **Syslogの確認とトラブルシューティング**

### 7. FHRP（First Hop Redundancy Protocol）
- **FHRPの概要と必要性**
  - デフォルトゲートウェイの冗長性
  - 高可用性の確保
- **FHRPの種類**
  - HSRP（Hot Standby Router Protocol）
  - VRRP（Virtual Router Redundancy Protocol）
  - GLBP（Gateway Load Balancing Protocol）
- **HSRPの設定**
  - グループ設定
  - プライオリティ
  - プリエンプション
  - 認証
- **VRRPの設定**
- **GLBPの設定**
- **FHRPの確認とトラブルシューティング**

## 実践演習
1. **Packet Tracerを使用したDHCPサーバーの設定と検証**
2. **NATの設定と検証（スタティック、ダイナミック、PAT）**
3. **NTPの設定と検証**
4. **SNMPの設定と検証**
5. **QoSの基本設定**
6. **HSRPの設定と検証**

## 参考リソース
- Cisco公式ドキュメント
- IPサービスに関する書籍
- オンライン学習リソース

## 学習の進捗
- [ ] DHCPの理解と設定
- [ ] NATの理解と設定
- [ ] NTPの理解と設定
- [ ] SNMPの理解と設定
- [ ] QoSの理解と基本設定
- [ ] Syslogの理解と設定
- [ ] FHRPの理解と設定
- [ ] 実践演習の完了
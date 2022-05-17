# A02:2021 – 暗号化の失敗    ![icon](assets/TOP_10_Icons_Final_Crypto_Failures.png){: style="height:80px;width:80px" align="right"}

## 因子

| 対応する CWE 数 | 最大発生率 | 平均発生率 |  加重平均（攻撃の難易度） | 加重平均（攻撃による影響） | 最大網羅率 | 平均網羅率 | 総発生数 | CVE 合計件数 |
|:-------------:|:--------------------:|:--------------------:|:--------------:|:--------------:|:----------------------:|:---------------------:|:-------------------:|:------------:|
| 29          | 46.44%             | 4.49%              |7.29                 | 6.81                |  79.33%       | 34.85%       | 233,788           | 3,075      |

## 概要

前回から順位を一つ上げたこのカテゴリは、以前は*機微な情報の露出*として知られていたものです。
このカテゴリは根本的な要因よりも、暗号化技術の不適切な使用、または暗号化の欠如に関連した幅広い障害に焦点を当てています。こうした障害は、時に機微な情報の露出を結果としてもたらします。
考慮すべき共通脆弱性タイプ一覧 (CWE)には、*CWE-259:ハードコードされたパスワードの使用*、*CWE-327:不適切な暗号化アルゴリズム*、*CWE-331:不十分なエントロピー*があります。

## 説明

まず、送信あるいは保存するデータが保護を必要とするか見極めます。例えば、パスワード、クレジットカード番号、健康記録、個人データやビジネス上の機密は特別な保護が必要になります。データに対して、EUの一般データ保護規則(GDPR)のようなプライバシー関連の法律が適用される場合、また、PCIデータセキュリティスタンダード(PCI DSS)など金融の情報保護の要求があるような規定がある場合には、特に注意が必要です。そのようなデータすべてについて、以下を確認してください:

-   どんなデータであれ平文で送信していないか。これは、HTTP、SMTP、FTP、あるいはSTARTTLSのようなTLS upgradesのプロトコルを使っている場合に該当する。外部インターネットへのトラフィックは危険である。また、ロードバランサー、Webサーバー、バックエンドシステムなどの内部の通信もすべて確認すること。

-   古いまたは脆弱な暗号アルゴリズムやプロトコルを初期設定のまま、または古いコードで使っていないか。

-   初期値のままの暗号鍵の使用、弱い暗号鍵を生成または再利用、適切な暗号鍵管理または鍵のローテーションをしていない、これらの該当する箇所はないか。暗号鍵がソースコードリポジトリに含まれていないか。

-   HTTPヘッダー（ブラウザ）のセキュリティに関するディレクティブやヘッダーが欠落しているなど、暗号化が強制されていない箇所はないか。

-   受け取ったサーバー証明書とその信頼チェーンが適切に検証されているか。

-   初期化ベクトルが無視されたり、再利用されたりしていないか。また、暗号利用モードにとって十分にセキュアではない状態で生成されていないか。
    ECBといった安全でないモードが使用されていないか。
    認証付き暗号がより適切な場合において、認証付き暗号でない暗号が使用されていないか。

-   鍵導出関数を使うことなしにパスワードを暗号鍵として使用していないか。

-   暗号学的要件を満たすように設計されていない目的でランダム性が使用されていないか。
    適切な関数が選ばれている場合でも、関数は開発者による初期化が必要か。
    必要でない場合、開発者が十分なエントロピーや予測不可能性を欠いたシードを用いて組み込みの強力な初期化機能を上書きしていないか。
    
-   MD5やSHA1といった非推奨のハッシュ関数が使用されていないか。また暗号学的ハッシュ関数が必要とされる場合において、暗号学的でないハッシュ関数が使用されていないか。

-   PKCS#1 v1.5といった非推奨の暗号学的パディング方式が使用されていないか。

-   暗号化時のエラーメッセージやサイドチャネルの情報が、パディングオラクル攻撃のような種類の攻撃に利用可能ではないか。

ASVS Crypto (V7)、Data Protection (V9)、および SSL/TLS (V10) を参照。

## 防止方法

最低限実施すべきことを以下に挙げます。そして、参考資料を検討してください:

-   アプリケーションごとに処理するデータ、保存するデータ、送信するデータを分類する。そして、どのデータがプライバシー関連の法律・規則の要件に該当するか、またどのデータがビジネス上必要なデータか判定する。

-   必要のない機微な情報を保存しない。できる限りすぐにそのような機微な情報を破棄するか、PCI DSSに準拠したトークナイゼーションまたはトランケーションを行う。データが残っていなければ盗まれない。

-   保存時にすべての機微な情報を暗号化しているか確認する。

-   最新の暗号強度の高い標準アルゴリズム、プロトコル、暗号鍵を実装しているか確認する。そして適切に暗号鍵を管理する。

-   前方秘匿性(FS)を有効にしたTLS、サーバーサイドによる暗号スイートの優先度決定、セキュアパラメータなどのセキュアなプロトコルで、通信経路上のすべてのデータを暗号化する。HTTP Strict Transport Security (HSTS)のようなディレクティブで暗号化を強制する。

-   機微な情報を含むレスポンスのキャッシングを無効にする。

-   データ分類に応じて必要なセキュリティ制御を適用する。

-   FTPやSMTPといったレガシーなプロトコルを機密データの伝送に使用しない。

-   パスワードを保存する際、Argon2、scrypt、bcrypt、PBKDF2のようなワークファクタ(遅延ファクタ)のある、強くかつ適応可能なレベルのソルト付きハッシュ関数を用いる。

-   初期化ベクトルは利用モードに応じて適切なものを選択しなければならない。これは多くのモードにおいてCSPRNG(暗号論的擬似乱数生成器)を使用することを意味する。
    nonceを必要とするモードの場合は、初期化ベクトル(IV)はCSPRNGを必要としない。
    すべての場合において、IVは単一の固定の鍵に対し二度使ってはならない。

-   単なる暗号ではなく、認証付き暗号を常に使用する。

-   鍵は暗号学的にランダムに生成し、またバイト配列としてメモリーに保存する。
    もしパスワードを使用する場合は、適切な鍵導出関数を用いて鍵へと変換されなければならない。

-   暗号学的乱数が適切な場所で使用されていること、またそれらが予測可能な方法や低いエントロピーによって初期化されていないことを確認する。
    多くのモダンなAPIでは、セキュリティを確保するために開発者がCSPRNGを初期化する必要はない。

-   MD5やSHA1、PKCS#1 v1.5といった非推奨の暗号学的関数やパディング方式の使用を避ける。

-   設定とその設定値がそれぞれ独立して効果があるか検証する。

## 攻撃シナリオの例

**シナリオ #1**: あるアプリケーションは、データベースの自動暗号化を使用し、クレジットカード番号を暗号化します。しかし、そのデータが取得されるときに自動的に復号されるため、SQLインジェクションによって平文のクレジットカード番号を取得できてしまいます。

**シナリオ #2**: あるサイトは、すべてのページでTLSを使っておらず、ユーザにTLSを強制していません。また、そのサイトでは弱い暗号アルゴリズムをサポートしています。攻撃者はネットワークトラフィックを監視し（例えば、暗号化していない無線ネットワークで）、HTTPS通信をHTTP通信にダウングレードしそのリクエストを盗聴することで、ユーザのセッションクッキーを盗みます。そして、攻撃者はこのクッキーを再送しユーザの(認証された)セッションを乗っ取り、そのユーザの個人データを閲覧および改ざんできます。また、攻撃者はセッションを乗っ取る代わりに、すべての送信データ（例えば、入金の受取人）を改ざんできます。

**シナリオ #3**: あるパスワードデータベースは、ソルトなしのハッシュまたは単純なハッシュでパスワードを保存しています。もしファイルアップロードの欠陥があれば、攻撃者はそれを悪用してパスワードデータベースを取得できます。事前に計算されたハッシュのレインボーテーブルで、すべてのソルトなしのハッシュが解読されてしまいます。そして、たとえソルトありでハッシュ化されていても、単純または高速なハッシュ関数で生成したハッシュはGPUで解読されてしまうかもしれません。

## 参考資料

-   [OWASP Proactive Controls: Protect Data
    Everywhere](https://owasp.org/www-project-proactive-controls/v3/en/c8-protect-data-everywhere)

-   [OWASP Application Security Verification Standard (V7,
    9, 10)](https://owasp.org/www-project-application-security-verification-standard)

-   [OWASP Cheat Sheet: Transport Layer
    Protection](https://cheatsheetseries.owasp.org/cheatsheets/Transport_Layer_Protection_Cheat_Sheet.html)

-   [OWASP Cheat Sheet: User Privacy
    Protection](https://cheatsheetseries.owasp.org/cheatsheets/User_Privacy_Protection_Cheat_Sheet.html)

-   [OWASP Cheat Sheet: Password and Cryptographic Storage](https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html)

-   [OWASP Cheat Sheet:
    HSTS](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html)

-   [OWASP Testing Guide: Testing for weak cryptography](https://owasp.org/www-project-web-security-testing-guide/stable/4-Web_Application_Security_Testing/09-Testing_for_Weak_Cryptography/README)


## 対応する CWE のリスト

[CWE-261 Weak Encoding for Password](https://cwe.mitre.org/data/definitions/261.html)

[CWE-296 Improper Following of a Certificate's Chain of Trust](https://cwe.mitre.org/data/definitions/296.html)

[CWE-310 Cryptographic Issues](https://cwe.mitre.org/data/definitions/310.html)

[CWE-319 Cleartext Transmission of Sensitive Information](https://cwe.mitre.org/data/definitions/319.html)

[CWE-321 Use of Hard-coded Cryptographic Key](https://cwe.mitre.org/data/definitions/321.html)

[CWE-322 Key Exchange without Entity Authentication](https://cwe.mitre.org/data/definitions/322.html)

[CWE-323 Reusing a Nonce, Key Pair in Encryption](https://cwe.mitre.org/data/definitions/323.html)

[CWE-324 Use of a Key Past its Expiration Date](https://cwe.mitre.org/data/definitions/324.html)

[CWE-325 Missing Required Cryptographic Step](https://cwe.mitre.org/data/definitions/325.html)

[CWE-326 Inadequate Encryption Strength](https://cwe.mitre.org/data/definitions/326.html)

[CWE-327 Use of a Broken or Risky Cryptographic Algorithm](https://cwe.mitre.org/data/definitions/327.html)

[CWE-328 Reversible One-Way Hash](https://cwe.mitre.org/data/definitions/328.html)

[CWE-329 Not Using a Random IV with CBC Mode](https://cwe.mitre.org/data/definitions/329.html)

[CWE-330 Use of Insufficiently Random Values](https://cwe.mitre.org/data/definitions/330.html)

[CWE-331 Insufficient Entropy](https://cwe.mitre.org/data/definitions/331.html)

[CWE-335 Incorrect Usage of Seeds in Pseudo-Random Number Generator(PRNG)](https://cwe.mitre.org/data/definitions/335.html)

[CWE-336 Same Seed in Pseudo-Random Number Generator (PRNG)](https://cwe.mitre.org/data/definitions/336.html)

[CWE-337 Predictable Seed in Pseudo-Random Number Generator (PRNG)](https://cwe.mitre.org/data/definitions/337.html)

[CWE-338 Use of Cryptographically Weak Pseudo-Random Number Generator(PRNG)](https://cwe.mitre.org/data/definitions/338.html)

[CWE-340 Generation of Predictable Numbers or Identifiers](https://cwe.mitre.org/data/definitions/340.html)

[CWE-347 Improper Verification of Cryptographic Signature](https://cwe.mitre.org/data/definitions/347.html)

[CWE-523 Unprotected Transport of Credentials](https://cwe.mitre.org/data/definitions/523.html)

[CWE-720 OWASP Top Ten 2007 Category A9 - Insecure Communications](https://cwe.mitre.org/data/definitions/720.html)

[CWE-757 Selection of Less-Secure Algorithm During Negotiation('Algorithm Downgrade')](https://cwe.mitre.org/data/definitions/757.html)

[CWE-759 Use of a One-Way Hash without a Salt](https://cwe.mitre.org/data/definitions/759.html)

[CWE-760 Use of a One-Way Hash with a Predictable Salt](https://cwe.mitre.org/data/definitions/760.html)

[CWE-780 Use of RSA Algorithm without OAEP](https://cwe.mitre.org/data/definitions/780.html)

[CWE-818 Insufficient Transport Layer Protection](https://cwe.mitre.org/data/definitions/818.html)

[CWE-916 Use of Password Hash With Insufficient Computational Effort](https://cwe.mitre.org/data/definitions/916.html)

# A02:2021 – Cryptographic Failures    ![icon](assets/TOP_10_Icons_Final_Crypto_Failures.png){: style="height:80px;width:80px" align="right"}

## Factors

| CWEs Mapped | Max Incidence Rate | Avg Incidence Rate | Avg Weighted Exploit | Avg Weighted Impact | Max Coverage | Avg Coverage | Total Occurrences | Total CVEs |
|:-------------:|:--------------------:|:--------------------:|:--------------:|:--------------:|:----------------------:|:---------------------:|:-------------------:|:------------:|
| 29          | 46.44%             | 4.49%              |7.29                 | 6.81                |  79.33%       | 34.85%       | 233,788           | 3,075      |

## Overview

Shifting up one position to #2, previously known as *Sensitive Data
Exposure*, which is more of a broad symptom rather than a root cause,
the focus is on failures related to cryptography (or lack thereof).
Which often lead to exposure of sensitive data. Notable Common Weakness Enumerations (CWEs) included
are *CWE-259: Use of Hard-coded Password*, *CWE-327: Broken or Risky
Crypto Algorithm*, and *CWE-331 Insufficient Entropy* .

## Description

The first thing is to determine the protection needs of data in transit
and at rest. For example, passwords, credit card numbers, health
records, personal information, and business secrets require extra
protection, mainly if that data falls under privacy laws, e.g., EU's
General Data Protection Regulation (GDPR), or regulations, e.g.,
financial data protection such as PCI Data Security Standard (PCI DSS).
For all such data:

-   Is any data transmitted in clear text? This concerns protocols such
    as HTTP, SMTP, FTP also using TLS upgrades like STARTTLS. External
    internet traffic is hazardous. Verify all internal traffic, e.g.,
    between load balancers, web servers, or back-end systems.

-   Are any old or weak cryptographic algorithms or protocols used either
    by default or in older code?

-   Are default crypto keys in use, weak crypto keys generated or
    re-used, or is proper key management or rotation missing?
    Are crypto keys checked into source code repositories?

-   Is encryption not enforced, e.g., are any HTTP headers (browser)
    security directives or headers missing?

-   Is the received server certificate and the trust chain properly validated?

-   Are initialization vectors ignored, reused, or not generated
    sufficiently secure for the cryptographic mode of operation?
    Is an insecure mode of operation such as ECB in use? Is encryption
    used when authenticated encryption is more appropriate?

-   Are passwords being used as cryptographic keys in absence of a
    password base key derivation function?

-   Is randomness used for cryptographic purposes that was not designed
    to meet cryptographic requirements? Even if the correct function is
    chosen, does it need to be seeded by the developer, and if not, has
    the developer over-written the strong seeding functionality built into
    it with a seed that lacks sufficient entropy/unpredictability?

-   Are deprecated hash functions such as MD5 or SHA1 in use, or are
    non-cryptographic hash functions used when cryptographic hash functions
    are needed?

-   Are deprecated cryptographic padding methods such as PKCS number 1 v1.5
    in use?

-   Are cryptographic error messages or side channel information
    exploitable, for example in the form of padding oracle attacks?

See ASVS Crypto (V7), Data Protection (V9), and SSL/TLS (V10)

## How to Prevent

Do the following, at a minimum, and consult the references:

-   Classify data processed, stored, or transmitted by an application.
    Identify which data is sensitive according to privacy laws,
    regulatory requirements, or business needs.

-   Don't store sensitive data unnecessarily. Discard it as soon as
    possible or use PCI DSS compliant tokenization or even truncation.
    Data that is not retained cannot be stolen.

-   Make sure to encrypt all sensitive data at rest.

-   Ensure up-to-date and strong standard algorithms, protocols, and
    keys are in place; use proper key management.

-   Encrypt all data in transit with secure protocols such as TLS with
    forward secrecy (FS) ciphers, cipher prioritization by the
    server, and secure parameters. Enforce encryption using directives
    like HTTP Strict Transport Security (HSTS).

-   Disable caching for response that contain sensitive data.

-   Apply required security controls as per the data classification.

-   Do not use legacy protocols such as FTP and SMTP for transporting
    sensitive data.

-   Store passwords using strong adaptive and salted hashing functions
    with a work factor (delay factor), such as Argon2, scrypt, bcrypt or
    PBKDF2.

-   Initialization vectors must be chosen appropriate for the mode of
    operation.  For many modes, this means using a CSPRNG (cryptographically
    secure pseudo random number generator).  For modes that require a
    nonce, then the initialization vector (IV) does not need a CSPRNG.  In all cases, the IV
    should never be used twice for a fixed key.

-   Always use authenticated encryption instead of just encryption.

-   Keys should be generated cryptographically randomly and stored in
    memory as byte arrays. If a password is used, then it must be converted
    to a key via an appropriate password base key derivation function.

-   Ensure that cryptographic randomness is used where appropriate, and
    that it has not been seeded in a predictable way or with low entropy.
    Most modern APIs do not require the developer to seed the CSPRNG to
    get security.

-   Avoid deprecated cryptographic functions and padding schemes, such as
    MD5, SHA1, PKCS number 1 v1.5 .

-   Verify independently the effectiveness of configuration and
    settings.

## Example Attack Scenarios

**Scenario #1**: An application encrypts credit card numbers in a
database using automatic database encryption. However, this data is
automatically decrypted when retrieved, allowing a SQL injection flaw to
retrieve credit card numbers in clear text.

**Scenario #2**: A site doesn't use or enforce TLS for all pages or
supports weak encryption. An attacker monitors network traffic (e.g., at
an insecure wireless network), downgrades connections from HTTPS to
HTTP, intercepts requests, and steals the user's session cookie. The
attacker then replays this cookie and hijacks the user's (authenticated)
session, accessing or modifying the user's private data. Instead of the
above they could alter all transported data, e.g., the recipient of a
money transfer.

**Scenario #3**: The password database uses unsalted or simple hashes to
store everyone's passwords. A file upload flaw allows an attacker to
retrieve the password database. All the unsalted hashes can be exposed
with a rainbow table of pre-calculated hashes. Hashes generated by
simple or fast hash functions may be cracked by GPUs, even if they were
salted.

## References

-   [OWASP Proactive Controls: Protect Data
    Everywhere](https://owasp.org/www-project-proactive-controls/v3/en/c8-protect-data-everywhere)

-   [OWASP Application Security Verification Standard (V7,
    9, 10)](https://owasp.org/www-project-application-security-verification-standard)

-   [OWASP Cheat Sheet: Transport Layer
    Protection](https://cheatsheetseries.owasp.org/cheatsheets/Transport_Layer_Protection_Cheat_Sheet.html)

-   [OWASP Cheat Sheet: User Privacy
    Protection](https://cheatsheetseries.owasp.org/cheatsheets/User_Privacy_Protection_Cheat_Sheet.html)

-   [OWASP Cheat Sheet: Password and Cryptographic Storage](https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html)

-   [OWASP Cheat Sheet:
    HSTS](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html)

-   [OWASP Testing Guide: Testing for weak cryptography](https://owasp.org/www-project-web-security-testing-guide/stable/4-Web_Application_Security_Testing/09-Testing_for_Weak_Cryptography/README)


## List of Mapped CWEs

[CWE-261 Weak Encoding for Password](https://cwe.mitre.org/data/definitions/261.html)

[CWE-296 Improper Following of a Certificate's Chain of Trust](https://cwe.mitre.org/data/definitions/296.html)

[CWE-310 Cryptographic Issues](https://cwe.mitre.org/data/definitions/310.html)

[CWE-319 Cleartext Transmission of Sensitive Information](https://cwe.mitre.org/data/definitions/319.html)

[CWE-321 Use of Hard-coded Cryptographic Key](https://cwe.mitre.org/data/definitions/321.html)

[CWE-322 Key Exchange without Entity Authentication](https://cwe.mitre.org/data/definitions/322.html)

[CWE-323 Reusing a Nonce, Key Pair in Encryption](https://cwe.mitre.org/data/definitions/323.html)

[CWE-324 Use of a Key Past its Expiration Date](https://cwe.mitre.org/data/definitions/324.html)

[CWE-325 Missing Required Cryptographic Step](https://cwe.mitre.org/data/definitions/325.html)

[CWE-326 Inadequate Encryption Strength](https://cwe.mitre.org/data/definitions/326.html)

[CWE-327 Use of a Broken or Risky Cryptographic Algorithm](https://cwe.mitre.org/data/definitions/327.html)

[CWE-328 Reversible One-Way Hash](https://cwe.mitre.org/data/definitions/328.html)

[CWE-329 Not Using a Random IV with CBC Mode](https://cwe.mitre.org/data/definitions/329.html)

[CWE-330 Use of Insufficiently Random Values](https://cwe.mitre.org/data/definitions/330.html)

[CWE-331 Insufficient Entropy](https://cwe.mitre.org/data/definitions/331.html)

[CWE-335 Incorrect Usage of Seeds in Pseudo-Random Number Generator(PRNG)](https://cwe.mitre.org/data/definitions/335.html)

[CWE-336 Same Seed in Pseudo-Random Number Generator (PRNG)](https://cwe.mitre.org/data/definitions/336.html)

[CWE-337 Predictable Seed in Pseudo-Random Number Generator (PRNG)](https://cwe.mitre.org/data/definitions/337.html)

[CWE-338 Use of Cryptographically Weak Pseudo-Random Number Generator(PRNG)](https://cwe.mitre.org/data/definitions/338.html)

[CWE-340 Generation of Predictable Numbers or Identifiers](https://cwe.mitre.org/data/definitions/340.html)

[CWE-347 Improper Verification of Cryptographic Signature](https://cwe.mitre.org/data/definitions/347.html)

[CWE-523 Unprotected Transport of Credentials](https://cwe.mitre.org/data/definitions/523.html)

[CWE-720 OWASP Top Ten 2007 Category A9 - Insecure Communications](https://cwe.mitre.org/data/definitions/720.html)

[CWE-757 Selection of Less-Secure Algorithm During Negotiation('Algorithm Downgrade')](https://cwe.mitre.org/data/definitions/757.html)

[CWE-759 Use of a One-Way Hash without a Salt](https://cwe.mitre.org/data/definitions/759.html)

[CWE-760 Use of a One-Way Hash with a Predictable Salt](https://cwe.mitre.org/data/definitions/760.html)

[CWE-780 Use of RSA Algorithm without OAEP](https://cwe.mitre.org/data/definitions/780.html)

[CWE-818 Insufficient Transport Layer Protection](https://cwe.mitre.org/data/definitions/818.html)

[CWE-916 Use of Password Hash With Insufficient Computational Effort](https://cwe.mitre.org/data/definitions/916.html)

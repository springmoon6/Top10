# 導入

## OWASP Top 10 - 2021 へようこそ

![OWASP Top 10 ロゴ](./assets/TOP_10_logo_Final_Logo_Colour.png){:class="img-responsive"}

OWASP トップ 10 の最新版へようこそ! OWASP トップ 10 2021年版は、グラフィックデザインが一新され、1ページのインフォグラフィックになっています。インフォグラフィックは、ホームページから入手でき、印刷することができます。

今回のトップ10の作成にあたって、貴重な時間やデータを提供してくださったすべての皆さんに感謝します。皆様のご協力なくしては、OWASP トップ 10 2021年版は存在し得ません。**本当に、感謝いたします**。

## 2021年版トップ10の変更点

2021年版トップ10では、3つの新しいカテゴリー、4つのカテゴリーの名称とスコープの変更がありました。統合されたものもいくつかあります。

![マッピング](assets/mapping.png)

- **A01:2021–アクセス制御の不備** は、5位から最も深刻なWebアプリケーションのセキュリティリスクへと順位を上げました。貢献されたデータから、平均でテストされたアプリケーションの3.81%が1つ以上の共通脆弱性タイプ一覧（CWE）を持っており、このリスクカテゴリに該当するCWEは 318,000 件以上存在していたことがわかりました。他のカテゴリーに比べ、「アクセス制御の欠陥」カテゴリにあたる34件のCWEがアプリケーション内で多く発生していました。
- **A02:2021–暗号化の失敗** は、ひとつ順位を上げて2位になっています。以前は、**A3:2017-機微な情報の露出** と呼ばれていましたが、これは根本的な原因というより幅広くみられる症状と言えます。ここでは、機密データの漏えいやシステム侵害に多く関連する、暗号技術にまつわる失敗に焦点を当てています。
- **A03:2021–インジェクション** は、3位に下がっています。94%のアプリケーションで何らかのインジェクションに関する問題が確認されています。最大発生率は19%、平均発生率は3.37%であり、このカテゴリにあたる33のCWEは、アプリケーションでの発生数が2番目に多く見られます。発生数は27万4千件でした。今回から、クロスサイトスクリプティングは、このカテゴリに含まれています。
- **A04:2021-安全が確認されない不安な設計** は、2021年に新設されたカテゴリーで、設計上の欠陥に関するリスクに焦点を当てています。一業界として、我々が純粋に「シフトレフト」することを望むのであれば、脅威モデリングや、安全な設計パターンと原則、また、リファレンス・アーキテクチャをもっと利用していくことが必要です。 安全が確認されない不安な設計は完璧な実装によって修正されることはありません。定義上、(つまり設計自体が問題なので)特定の攻撃に対して必要なセキュリティ対策が作られることがありえないからです。
- **A05:2021-セキュリティの設定ミス** は、前回の6位から順位を上げました。アプリケーションの90％に何らかの設定ミスが見られ、インシデントの平均発生率としては4.5%、このリスクカテゴリに該当するCWEは 208,000 件以上存在していたことがわかりました。 高度な設定が可能なソフトウェアへの移行が進む中で、このカテゴリーの順位が上がったことは当然と言えます。以前の、**A4:2017-XML 外部エンティティ参照 (XXE)** のカテゴリーは、このカテゴリーに含まれています。
- **A06:2021–脆弱で古くなったコンポーネント** は、以前は「既知の脆弱性のあるコンポーネントの使用」というタイトルでした。この問題は、Top 10コミュニティの調査では2位であり、データ分析によってトップ10に入るだけのデータもありました。このカテゴリーは2017年の9位から順位を上げました。これは、テストやリスク評価に苦労する、よく知られた問題です。また、含まれるCWEにあたる共通脆弱性識別子 (CVE)のない、唯一のカテゴリであるため、デフォルトのエクスプロイトとインパクトの重みは5.0としてスコアに反映されています。
- **A07:2021–識別と認証の失敗** は以前、「認証の不備」と呼ばれていましたが、この版では第2位から順位を落とし、識別の失敗に関連するCWEをより多く含む意味合いのカテゴリとなっています。このカテゴリーは依然としてトップ10に示すべき重要な項目ですが、標準化されたフレームワークの利用が進んだことが功を奏しているようです。
- **A08:2021–ソフトウェアとデータの整合性の不具合** は、2021年に新設されたカテゴリーで、ソフトウェアの更新、重要なデータを、CI/CDパイプラインにおいて整合性を検証せずに見込みで進めることによる問題にフォーカスしています。共通脆弱性識別子/共通脆弱性評価システム (CVE/CVSS) のデータから最も重大な影響を受けたものの1つが、このカテゴリーの10のCWEにマッピングされています。**A8:2017-安全でないデシリアライゼーション** は、このカテゴリーの一部となりました。
- **A09:2021–セキュリティログとモニタリングの失敗** は、従来は**A10:2017-不十分なロギングとモニタリング**でしたが、Top 10コミュニティの調査（第3位）から追加され、従来の第10位からランクアップしました。このカテゴリは、より多くの種類の失敗を含むように拡張されています。これは、テストが困難なものであり、かつ、CVE/CVSSのデータにはあまり反映されないものです。とはいえ、このカテゴリーで失敗が起きると、可視性、インシデントアラート、フォレンジックなどに直接影響を与える可能性があります。
- **A10:2021-サーバーサイドリクエストフォージェリ (SSRF)** は、Top 10コミュニティの調査（第1位）から追加されたものです。調査データからわかることは、よくあるテストより広範な範囲において、問題の発生率は比較的低いものの、問題が起きた場合のエクスプロイトとインパクトは平均以上のものとなり得ます。このカテゴリは、現時点でデータとして現れるものではありませんでしたが、複数の業界の専門家により重要との示唆を得たシナリオとして反映しています。

## 方法論

今回のトップ10は、これまで以上にデータを重視していますが、やみくもにデータを重視しているわけではありません。10項目のうち8項目は提供されたデータから、2項目はTop 10コミュニティの調査から高いレベルで選びました。こうすることにはひとつの根本的な理由があります。提供されたデータを見ることは、過去を見ることを意味している、ということです。アプリケーションセキュリティのリサーチャーが新しい脆弱性や、それをテストする新しい方法を見つけるのには時間がかかります。これらのテストをツールやプロセスに組み込むには時間がかかります。こうした弱点を広く確実にテストできるようになるまでには、何年もかかってしまうことでしょう。そこで、データではわからないような本質的な弱点は何かということについては、業界の第一線で活躍されている方々にお聞きすることでバランスをとる、というわけです。

トップ10を継続的に成熟させるために私たちが採用した、重要な変更点がいくつかあります。

## カテゴリの構成について

前回のOWASP Top 10からいくつかのカテゴリーが変更されています。以下に今回のカテゴリーの変更点を大まかにまとめます。

前回のデータ収集活動は、約30個のCWEからなる規定のサブセットに焦点を当て、追加として現場での調査結果を求めていました。この方法では、現場の組織は、主にこのリクエストした30のCWEだけに焦点を当てて報告をくれることになり、実際に観察したCWEを追加してくれることはまれだということがわかりました。そこで今回は、リクエストするCWEに制限を設けずに、データを提供してもらうことにしました。ある年に（今回は2017年以降）テストしたアプリケーションの数と、テストでCWE登録されている例が1つ以上見つかったアプリケーションの数を出してくれるよう依頼しました。これにより、アプリケーション全体を母集団としてとった上で、それぞれのCWEがどの程度蔓延しているかを把握することができます。

目的を踏まえて、当該CWEの発見頻度については無視しました。頻度は他の状況では必要性があるかもしれませんが、アプリケーションの母集団においては、現実の蔓延率を隠すことになってしまいます。例えば、あるアプリケーションに、ある特定のCWEの脆弱性が4例見つかることもあれば、4,000例見つかることもあるかもしれませんが、その発生頻度はトップ10の計算に影響させないというわけです。こうして、データセットで分析できたCWEは約30個から約400個になりました。今後、私たちは追加のデータ解析を行い、Top 10に補足する計画です。このようにCWEの数が大幅に増えたことで、カテゴリーの構成方法を変更する必要があります。

CWEのグループ化と分類に数ヶ月を費やしました。さらに数ヶ月続けることもできたかもしれませんが、どこかの時点で止めなければなりません。CWEには「根本原因」と「症状」があり、「根本原因」には「暗号の欠陥」や「設定ミス」などがあり、「症状」には「機密データの漏えい」や「サービス妨害」などがあります。そこで私たちは、可能な限り根本的な原因に焦点を当てることにしました。識別と修復のためのガイダンスを提供するのに適しているからです。「症状」ではなく「根本原因」に焦点を当てることは、今に始まったコンセプトではありません。どの版のTop 10も、症状と原因が混在してきました。CWEもまた、「症状」と「根本原因」が混在しています。私たちはそのことをより慎重に考え、呼びかけています。今回のカテゴリごとに含まれるCWE数は平均19.6件で、最少で **A10:2021-サーバーサイドリクエストフォージェリ(SSRF)** の1件、そして最多のものは **A04:2021-安全が確認されない不安な設計** の40件となっています。このカテゴリー構造の変更はトレーニングにさらなる効果をもたらします。たとえば企業は、利用している言語やフレームワークにとって意味のあるCWEに集中して教えることができるでしょう。

## カテゴリ選定にデータがどのように使用されたか

2017年では、発生率よりカテゴリーを選定して可能性を判断し、数十年の経験に基づき、*悪用のしやすさ*、*検出のしやすさ*(および *可能性*)、*技術面への影響*についてチームの議論によりランク付けしました。2021年については、可能であれば*悪用のしやすさ*と*(技術面の) 影響*のデータを使用したいと思います。

OWASP Dependency Checkをダウンロードし、CVSS Exploit、およびImpactのスコアを、関連するCWEでグループ化して抽出しました。CVSSv2にはCVSSv3で対処されるであろう欠陥があるにもかかわらず、すべてのCVEはCVSSv2のスコアを持っていたため、かなりの調査と労力を要しました。ですがある時点から、すべてのCVEにCVSSv3のスコアも割り当てられるようになりました。なお、CVSSv2とCVSSv3の間では、スコアの範囲と計算式が更新されています。

CVSSv2 では、*悪用性* と *(技術面の) 影響* の両方が 10.0 まで可能でしたが、計算式によって *悪用性* は 60%、*影響* は 40% に調整されました。CVSSv3では、理論的な最大値が*Exploit*が6.0、*Impact*が4.0に制限されています。この重み付けにより、CVSSv3ではインパクトのスコアが平均でほぼ1.5ポイント高くなり、悪用性のスコアは平均でほぼ0.5ポイント低くなりました。

OWASP Dependency Checkから抽出されたNVD（National Vulnerability Database）データには、CWEがマッピングされたCVEのレコードは125,000件あり、これらの中に一意のCWEは241件確認されました。CWEがマップされた 6,200件がCVSSv3スコアを持っており、これはデータセットの母数の約半分に相当します。

2021年版Top10では、以下の方法で平均*悪用性*スコアと*影響*スコアを算出しました。CVSSスコアを持つすべてのCVEをCWEでグループ化し、*悪用性*と*影響*の両スコアを、CVSSv3スコアを持つ母集団の割合 + CVSSv2スコアを持つ残りの母集団で重み付けして全体の平均値を算出しました。この平均値をデータセットのCWEにマッピングし、リスク方程式のうち半分の*悪用性*および*(技術面の) 影響*スコアとして使用しました。

## なぜ純粋な統計データだけではないのか

データからの結果は、主に自動化された方法でテストできるものからに限られています。しかし、経験豊富なAppSecの専門家に話を聞けば、まだデータにはない発見や傾向について教えてくれるでしょう。とはいえ特定の脆弱性タイプに対するテスト手法を開発するのには時間が必要です。そのテストを自動化し、多くのアプリケーションに対して自動的に実行できるようにするのは、さらに時間がかかります。つまり、データから過去を振り返るだけでは限界があり、データにはない昨年のトレンドを見落としている可能性があります。

そのため、不完全ともいえるデータの結果からのカテゴリ選定は10項目のうち8項目に留めています。残りの2つのカテゴリーは、トップ10コミュニティ調査によって選びました。これは、最前線で実際に活躍されている方々が、最も高いリスクにもかかわらず、データには現れないであろう（データでは表しようもない）と思われるものを選んでくれたものです。

## 頻度ではなく、発生率を基準とした理由

データソースは主に3つあります。ここでは、HaT（Human-assisted Tooling:人間援助型自動テスト）、TaH（Tool-assisted Human:ツールを利用した手動テスト）、そしてRaw Tooling:完全自動テストと名付けました。

自動テストとHaTは高頻度発見生成機です。これらは、特定の脆弱性に対して、その脆弱性を持つすべてのインスタンスをできる限り見つけようとします。このため、いくつかの脆弱性のタイプについて高い発見数を出力します。クロスサイトスクリプティングを例にしますと、この脆弱性は通常、軽微で孤立したミスによるものとシステム的な問題によるもの、の2種類があります。システム的な問題である場合、単一のアプリケーションで発見数が数千になることがあります。このようなデータで他のレポートやデータから発見された他のほとんどの脆弱性が埋もれてしまいます。

一方、TaHでは、より幅広い種類の脆弱性を発見しますが、時間の制約上、発見頻度はかなり低くなります。人間がアプリケーションをテストしてクロスサイトスクリプティングといったものを発見した場合、通常3つか4つのインスタンスを発見して切り上げます。この時点でシステム的な発見を判断し、アプリケーション全体のスケールで修正するための推奨事項とともに、レポートを書き上げることができます。すべてのインスタンスを見つけることは(それにかける時間も)必要ありません。

この2つの異なるデータセットを取り出して、頻度の観点でマージしようとしたとします。その場合、自動テストとHaTのデータで、より正確で（ただし広く薄い）TaHのデータを埋もれてしまうでしょう。これがクロスサイトスクリプティングのように、影響は一般的に小さいか中程度であるようなものが、多くのリストにおいて高い順位に挙げられている理由の一つです。つまりまさしく発見が非常に多いからです。(クロスサイトスクリプティングはテストもしやすいので、それに対するテストも多く行われています）。

2017年には、データを改めて見直し自動テスト及びHaTのデータをTaHのデータときれいに統合するために、代わりに発生率を用いることを導入しました。発生率とは、ある脆弱性タイプのインスタンスを一つ以上持っていたものが、アプリケーションの母集団のうち何％いたかを確認したものです。単発的なものかシステム的なものかは気にしません。それは私たちの目的に影響しないからです。つまり少なくとも1つのインスタンスを持つアプリケーションの数が分かればよいだけなのです。これは、高頻度の結果でデータを埋もれさせることなく、複数のテストタイプにまたがるテストの所見をより明確に示すのに役立ちます。リスク分析観点として、攻撃者はたった1つの脆弱なインスタンスがありさえすれば、カテゴリを経由してアプリケーション攻撃成功できる、ということにもあたります。 

## データの収集と分析のプロセスについて

2017年のオープンセキュリティサミットでOWASP Top 10のデータ収集プロセスを正式化しました。OWASP Top 10のリーダーとコミュニティは、2日間かけて透明性のあるデータ収集プロセスを正式化することに取り組みました。2021年版は、このプロセスを利用した2回目の取り組みになります。

私たちは、ソーシャルメディアのチャンネルを通じて、OWASPプロジェクトとOWASPのGithub両方でデータの募集を公表しています。OWASPプロジェクトのページでは、私たちが求めているデータの要素や構造、そして提出方法をリストアップしています。GitHubプロジェクトでは、テンプレートとなるサンプルファイルを用意しています。必要に応じて組織と協力し、構造の解析やCWEへのマッピングを行っています。

ベンダーのテスト業務を生業とする組織、バグバウンティベンダー、社内のデータテスト結果を提供してくれた組織などからデータを入手します。データを入手したら、それを読み込んで、どのようなCWEがどのリスクカテゴリにマッピングされるかを根本的に分析します。CWEの中にはリスクカテゴリが重複しているものもあれば、非常に密接に別のリスクカテゴリに関連しているものもあります（例：暗号の脆弱性）。提出された生データに関する決定はすべて文書化され、オープンとなるよう公開し、データをどのように正規化したかについて透明性のあるものとしています。

トップ10に含めるために、発生率の高い8つのカテゴリーを調べます。また、トップ10のコミュニティアンケート結果を見て、すでにデータとして確認できているであろうものを確認します。そうしてデータからは確認できなかった上位2つを、Top10の残りの2箇所に選びます。10個すべてが選ばれたら、トップ10をリスクに基づく順序でランク付けするのに役立てるべく、悪用のしやすさと影響に関する一般要素をあてはめました。

## 用語集

トップ10カテゴリーのそれぞれの中にある下記用語について、意味を記載します。

- CWEs Mapped(カテゴリにあたるCWEの数): Top10チームがカテゴリーにマッピングしたCWEの数です。
- Incidence Rate(発生率): 発生率とは、当年に機関によってテストされた母集団のうち、カテゴリにマップされたCWEに脆弱なアプリケーションの割合を示します。
- (Testing) Coverage(テスト)網羅範囲: カテゴリにマップされたCWEに対して、機関がテストできたアプリケーションの範囲。
- Weighted Exploit(重み付けされた悪用性): CVEに割り当てられているCVSSv2およびCVSSv3スコアの悪用性サブスコアを正規化し、10ptのスケールで表示したものです。
- Weighted Impact(重み付けされた影響度): CVEに割り当てられているCVSSv2およびCVSSv3スコアの影響サブスコアを正規化し、10ptのスケールで表示したものです。
- Total Occurrences(総発生数): カテゴリにマッピングされたCWEを持つことが判明したアプリケーションの総数です。
- Total CVEs(CVE合計数): カテゴリにマッピングされたCWEに該当する、NVD DB内のCVEの総数です。


## データ貢献者への謝辞

この最も大規模で包括的なアプリケーションセキュリティのデータセットを作り上げるために、（何名かの匿名の提供者とともに）以下の組織には 50,000 を超えるアプリケーションに関するデータを提供いただきました。 これは皆様のご協力なくしては成し得ませんでした。

- AppSec Labs
- Cobalt.io
- Contrast Security
- GitLab
- HackerOne
- HCL Technologies
- Micro Focus
- PenTest-Tools
- Probely
- Sqreen
- Veracode
- WhiteHat (NTT)

## スポンサーの方への謝辞

OWASP Top 10 2021 チームは、資金面での援助をいただいた Secure Code Warrior および Just Eat に心より感謝いたします。

[![Secure Code Warrior](assets/securecodewarrior.png){ width="256" }](https://securecodewarrior.com)    

[![Just Eats](assets/JustEat.png){ width="256" }](https://www.just-eat.co.uk/)

# Introduction

## Welcome to the OWASP Top 10 - 2021

![OWASP Top 10 Logo](./assets/TOP_10_logo_Final_Logo_Colour.png){:class="img-responsive"}

Welcome to the latest installment of the OWASP Top 10! The OWASP Top 10 2021 is all-new, with a new graphic design and an available one-page infographic you can print or obtain from our home page.

A huge thank you to everyone that contributed their time and data for this iteration. Without you, this installment would not happen. **THANK YOU!**

## What's changed in the Top 10 for 2021

There are three new categories, four categories with naming and scoping changes, and some consolidation in the Top 10 for 2021. We've changed names when necessary to focus on the root cause over the symptom.

![Mapping](assets/mapping.png)

- **A01:2021-Broken Access Control** moves up from the fifth position to the category with the most serious web application security risk; the contributed data indicates that on average, 3.81% of applications tested had one or more Common Weakness Enumerations (CWEs) with more than 318k occurrences of CWEs in this risk category. The 34 CWEs mapped to Broken Access Control had more occurrences in applications than any other category.
- **A02:2021-Cryptographic Failures** shifts up one position to #2, previously known as **A3:2017-Sensitive Data Exposure**, which was broad symptom rather than a root cause. The renewed name focuses on failures related to cryptography as it has been implicitly before. This category often leads to sensitive data exposure or system compromise.
- **A03:2021-Injection** slides down to the third position. 94% of the applications were tested for some form of injection with a max incidence rate of 19%, an average incidence rate of 3.37%, and the 33 CWEs mapped into this category have the second most occurrences in applications with 274k occurrences. Cross-site Scripting is now part of this category in this edition.
- **A04:2021-Insecure Design** is a new category for 2021, with a focus on risks related to design flaws. If we genuinely want to "move left" as an industry, we need more threat modeling, secure design patterns and principles, and reference architectures. An insecure design cannot be fixed by a perfect implementation as by definition, needed security controls were never created to defend against specific attacks.
- **A05:2021-Security Misconfiguration** moves up from #6 in the previous edition; 90% of applications were tested for some form of misconfiguration, with an average incidence rate of 4.5%, and over 208k occurrences of CWEs mapped to this risk category. With more shifts into highly configurable software, it's not surprising to see this category move up. The former category for **A4:2017-XML External Entities (XXE)** is now part of this risk category.
- **A06:2021-Vulnerable and Outdated Components** was previously titled Using Components with Known Vulnerabilities and is #2 in the Top 10 community survey, but also had enough data to make the Top 10 via data analysis. This category moves up from #9 in 2017 and is a known issue that we struggle to test and assess risk. It is the only category not to have any Common Vulnerability and Exposures (CVEs) mapped to the included CWEs, so a default exploit and impact weights of 5.0 are factored into their scores.
- **A07:2021-Identification and Authentication Failures** was previously Broken Authentication and is sliding down from the second position, and now includes CWEs that are more related to identification failures. This category is still an integral part of the Top 10, but the increased availability of standardized frameworks seems to be helping.
- **A08:2021-Software and Data Integrity Failures** is a new category for 2021, focusing on making assumptions related to software updates, critical data, and CI/CD pipelines without verifying integrity. One of the highest weighted impacts from Common Vulnerability and Exposures/Common Vulnerability Scoring System (CVE/CVSS) data mapped to the 10 CWEs in this category. **A8:2017-Insecure Deserialization** is now a part of this larger category.
- **A09:2021-Security Logging and Monitoring Failures** was previously **A10:2017-Insufficient Logging & Monitoring** and is added from the Top 10 community survey (#3), moving up from #10 previously. This category is expanded to include more types of failures, is challenging to test for, and isn't well represented in the CVE/CVSS data. However, failures in this category can directly impact visibility, incident alerting, and forensics.
- **A10:2021-Server-Side Request Forgery** is added from the Top 10 community survey (#1). The data shows a relatively low incidence rate with above average testing coverage, along with above-average ratings for Exploit and Impact potential. This category represents the scenario where the security community members are telling us this is important, even though it's not illustrated in the data at this time.

## Methodology

This installment of the Top 10 is more data-driven than ever but not blindly data-driven. We selected eight of the ten categories from contributed data and two categories from the Top 10 community survey at a high level. We do this for a fundamental reason, looking at the contributed data is looking into the past. AppSec researchers take time to find new vulnerabilities and new ways to test for them. It takes time to integrate these tests into tools and processes. By the time we can reliably test a weakness at scale, years have likely passed. To balance that view, we use a community survey to ask application security and development experts on the front lines what they see as essential weaknesses that the data may not show yet.

There are a few critical changes that we adopted to continue to mature the Top 10.

## How the categories are structured

A few categories have changed from the previous installment of the OWASP Top Ten. Here is a high-level summary of the category changes.

Previous data collection efforts were focused on a prescribed subset of approximately 30 CWEs with a field asking for additional findings. We learned that organizations would primarily focus on just those 30 CWEs and rarely add additional CWEs that they saw. In this iteration, we opened it up and just asked for data, with no restriction on CWEs. We asked for the number of applications tested for a given year (starting in 2017), and the number of applications with at least one instance of a CWE found in testing. This format allows us to track how prevalent each CWE is within the population of applications. We ignore frequency for our purposes; while it may be necessary for other situations, it only hides the actual prevalence in the application population. Whether an application has four instances of a CWE or 4,000 instances is not part of the calculation for the Top 10. We went from approximately 30 CWEs to almost 400 CWEs to analyze in the dataset. We plan to do additional data analysis as a supplement in the future. This significant increase in the number of CWEs necessitates changes to how the categories are structured.

We spent several months grouping and categorizing CWEs and could have continued for additional months. We had to stop at some point. There are both *root cause* and *symptom* types of CWEs, where *root cause* types are like "Cryptographic Failure" and "Misconfiguration" contrasted to *symptom* types like "Sensitive Data Exposure" and "Denial of Service." We decided to focus on the *root cause* whenever possible as it's more logical for providing identification and remediation guidance. Focusing on the *root cause* over the *symptom* isn't a new concept; the Top Ten has been a mix of *symptom* and *root cause*. CWEs are also a mix of *symptom* and *root cause*; we are simply being more deliberate about it and calling it out. There is an average of 19.6 CWEs per category in this installment, with the lower bounds at 1 CWE for **A10:2021-Server-Side Request Forgery (SSRF)** to 40 CWEs in **A04:2021-Insecure Design**. This updated category structure offers additional training benefits as companies can focus on CWEs that make sense for a language/framework.

## How the data is used for selecting categories

In 2017, we selected categories by incidence rate to determine likelihood, then ranked them by team discussion based on decades of experience for *Exploitability*, *Detectability* (also *likelihood*), and *Technical Impact*. For 2021, we want to use data for *Exploitability* and *(Technical) Impact* if possible.

We downloaded OWASP Dependency Check and extracted the CVSS Exploit, and Impact scores grouped by related CWEs. It took a fair bit of research and effort as all the CVEs have CVSSv2 scores, but there are flaws in CVSSv2 that CVSSv3 should address. After a certain point in time, all CVEs are assigned a CVSSv3 score as well. Additionally, the scoring ranges and formulas were updated between CVSSv2 and CVSSv3.

In CVSSv2, both *Exploit* and *(Technical) Impact* could be up to 10.0, but the formula would knock them down to 60% for *Exploit* and 40% for *Impact*. In CVSSv3, the theoretical max was limited to 6.0 for *Exploit* and 4.0 for *Impact*. With the weighting considered, the Impact scoring shifted higher, almost a point and a half on average in CVSSv3, and exploitability moved nearly half a point lower on average.

There are 125k records of a CVE mapped to a CWE in the National Vulnerability Database (NVD) data extracted from OWASP Dependency Check, and there are 241 unique CWEs mapped to a CVE. 62k CWE maps have a CVSSv3 score, which is approximately half of the population in the data set.

For the Top Ten 2021, we calculated average *exploit* and *impact* scores in the following manner. We grouped all the CVEs with CVSS scores by CWE and weighted both *exploit* and *impact* scored by the percentage of the population that had CVSSv3 + the remaining population of CVSSv2 scores to get an overall average. We mapped these averages to the CWEs in the dataset to use as *Exploit* and *(Technical) Impact* scoring for the other half of the risk equation.

## Why not just pure statistical data?

The results in the data are primarily limited to what we can test for in an automated fashion. Talk to a seasoned AppSec professional, and they will tell you about stuff they find and trends they see that aren't yet in the data. It takes time for people to develop testing methodologies for certain vulnerability types and then more time for those tests to be automated and run against a large population of applications. Everything we find is looking back in the past and might be missing trends from the last year, which are not present in the data.

Therefore, we only pick eight of ten categories from the data because it's incomplete. The other two categories are from the Top 10 community survey. It allows the practitioners on the front lines to vote for what they see as the highest risks that might not be in the data (and may never be expressed in data).

## Why incidence rate instead of frequency?

There are three primary sources of data. We identify them as Human-assisted Tooling (HaT), Tool-assisted Human (TaH), and raw Tooling.

Tooling and HaT are high-frequency finding generators. Tools will look for specific vulnerabilities and tirelessly attempt to find every instance of that vulnerability and will generate high finding counts for some vulnerability types. Look at Cross-Site Scripting, which is typically one of two flavors: it's either a more minor, isolated mistake or a systemic issue. When it's a systemic issue, the finding counts can be in the thousands for a single application. This high frequency drowns out most other vulnerabilities found in reports or data.

TaH, on the other hand, will find a broader range of vulnerability types but at a much lower frequency due to time constraints. When humans test an application and see something like Cross-Site Scripting, they will typically find three or four instances and stop. They can determine a systemic finding and write it up with a recommendation to fix on an application-wide scale. There is no need (or time) to find every instance.

Suppose we take these two distinct data sets and try to merge them on frequency. In that case, the Tooling and HaT data will drown the more accurate (but broad) TaH data and is a good part of why something like Cross-Site Scripting has been so highly ranked in many lists when the impact is generally low to moderate. It's because of the sheer volume of findings. (Cross-Site Scripting is also reasonably easy to test for, so there are many more tests for it as well).

In 2017, we introduced using incidence rate instead to take a fresh look at the data and cleanly merge Tooling and HaT data with TaH data. The incidence rate asks what percentage of the application population had at least one instance of a vulnerability type. We don't care if it was one-off or systemic. That's irrelevant for our purposes; we just need to know how many applications had at least one instance, which helps provide a clearer view of the testing is findings across multiple testing types without drowning the data in high-frequency results. This corresponds to a risk related view as an attacker needs only one instance to attack an application successfully via the category.

## What is your data collection and analysis process?

We formalized the OWASP Top 10 data collection process at the Open Security Summit in 2017. OWASP Top 10 leaders and the community spent two days working out formalizing a transparent data collection process. The 2021 edition is the second time we have used this methodology.

We publish a call for data through social media channels available to us, both project and OWASP. On the OWASP Project page, we list the data elements and structure we are looking for and how to submit them. In the GitHub project, we have example files that serve as templates. We work with organizations as needed to help figure out the structure and mapping to CWEs.

We get data from organizations that are testing vendors by trade, bug bounty vendors, and organizations that contribute internal testing data. Once we have the data, we load it together and run a fundamental analysis of what CWEs map to risk categories. There is overlap between some CWEs, and others are very closely related (ex. Cryptographic vulnerabilities). Any decisions related to the raw data submitted are documented and published to be open and transparent with how we normalized the data.

We look at the eight categories with the highest incidence rates for inclusion in the Top 10. We also look at the Top 10 community survey results to see which ones may already be present in the data. The top two votes that aren't already present in the data will be selected for the other two places in the Top 10. Once all ten were selected, we applied generalized factors for exploitability and impact; to help rank the Top 10 2021 in a risk based order.

## Data Factors

There are data factors that are listed for each of the Top 10 Categories, here is what they mean:

- CWEs Mapped: The number of CWEs mapped to a category by the Top 10 team.
- Incidence Rate: Incidence rate is the percentage of applications vulnerable to that CWE from the population tested by that org for that year.
- Weighted Exploit: The Exploit sub-score from CVSSv2 and CVSSv3 scores assigned to CVEs mapped to CWEs, normalized, and placed on a 10pt scale.
- Weighted Impact: The Impact sub-score from CVSSv2 and CVSSv3 scores assigned to CVEs mapped to CWEs, normalized, and placed on a 10pt scale.
- (Testing) Coverage: The percentage of applications tested by all organizations for a given CWE.
- Total Occurrences: Total number of applications found to have the CWEs mapped to a category.
- Total CVEs: Total number of CVEs in the NVD DB that were mapped to the CWEs mapped to a category.


## Thank you to our data contributors

The following organizations (along with some anonymous donors) kindly donated data for over 500,000 applications to make this the largest and most comprehensive application security data set. Without you, this would not be possible.

- AppSec Labs
- Cobalt.io
- Contrast Security
- GitLab
- HackerOne
- HCL Technologies
- Micro Focus
- PenTest-Tools
- Probely
- Sqreen
- Veracode
- WhiteHat (NTT)

## Thank you to our sponsor

The OWASP Top 10 2021 team gratefully acknowledge the financial support of Secure Code Warrior and Just Eat.

[![Secure Code Warrior](assets/securecodewarrior.png){ width="256" }](https://securecodewarrior.com)    

[![Just Eats](assets/JustEat.png){ width="256" }](https://www.just-eat.co.uk/)
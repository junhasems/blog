---
title: セキュアなコラボレーションを実現するクロス テナント アクセス設定が一般公開されました！
date: 2022-08-09 09:00
tags:
    - Azure AD
    - US Identity Blog
---

こんにちは、 Azure Identity サポート チームの小出です。

本記事は、 2022 年 7 月 21 日に米国の Azure Active Directory Identity Blog で公開された [Cross-tenant access settings for secure collaboration now generally available!](https://techcommunity.microsoft.com/t5/microsoft-entra-azure-ad-blog/cross-tenant-access-settings-for-secure-collaboration-now/ba-p/3575844) を意訳したものになります。ご不明点などございましたら、サポート チームまでお問い合わせください。

---

# セキュアなコラボレーションを実現するクロス テナント アクセス設定が一般公開されました！

みなさん、こんにちは。 

外部コラボレーションのためのクロス テナント アクセス設定が、一般利用可能になったことをお伝えしたいと思います。セキュアなコラボレーション ポリシーを実現するためにチームが行った作業を誇りに思うと同時に、[パブリック プレビュー](https://techcommunity.microsoft.com/t5/microsoft-entra-azure-ad-blog/collaborate-more-securely-with-new-cross-tenant-access-settings/ba-p/2147077) を実施した際に、お客様から得た知見を共有できることを嬉しく思います。

お客様からお聞きした採用事例やメインのシナリオについて、ここからはシニア プロダクト マネージャーの Josh Douglas を迎えて、話を聞きたいと思います。

----

Robin、ありがとう! クロス テナント アクセス設定と一般提供までの道のりについて、皆さんに詳しくお話できることをうれしく思います。パブリック プレビューでは、多くのお客様がクロス テナント アクセス設定を採用し、以前は不可能だったシナリオや要件に対応されています。このことを説明するために、まずは以下の情報を紹介します。

- 5,000 以上のテナントが、他の組織のために MFA の信頼を設定しました。
- 2,000 以上のテナントが、準拠済みもしくは Azure AD 参加デバイスの信頼関係を構成しました。

これらの統計は、この機能によって、従来は不可能だった組織外のコラボレーションのセキュリティ確保が可能になるという、皆様からの素晴らしいフィードバックに沿うものです。

## セキュアなコラボレーションを実現しながら外部ユーザーとスムーズに連携する

外部ユーザーの MFA 登録を管理することで、追加作業が発生し、サポート コストが増加するという声が聞かれます。さらにユーザーは、コラボレーションする異なる組織間で、時には複数回、登録と MFA を実行しなければならず負担を感じていました。受信方向のクロス テナント アクセス設定では、外部の Azure AD 組織からの MFA のセキュリティ クレームを信頼し、条件付きアクセス ポリシーで MFA が要求された場合に、外部ユーザーがホーム テナントで MFA を実行するようにするお客様が多くなっています。これにより、ユーザーは別のテナントのリソースにアクセスする際に 2 回目の MFA を実行する必要がなくなり、ユーザーにとっての負担が大幅に軽減されます。これにより、組織で要求されるセキュリティ体制を維持しながら、外部ユーザーの MFA 登録を管理する必要がなくなり、サポート コストを削減することができます。また、組織で発生する MFA コストも削減できます。

さらに、外部ユーザーがアプリやリソースにアクセスするデバイスの種類を懸念しているお客様もいらっしゃいました。条件付きアクセス ポリシーを適用して、外部ユーザーが準拠済みデバイスまたはハイブリッド Azure AD 参加ドメインでリソースにアクセスすることを要求することが、受信方向のクロス テナント アクセス設定で可能になりました。外部 AD 組織からのデバイス クレームを信頼することで、管理されたデバイスで外部ユーザーがアプリやリソースにアクセスしていることがわかり、データをさらに保護することができます。 

詳細は [External Identities の認証と条件付きアクセス](https://docs.microsoft.com/ja-jp/azure/active-directory/external-identities/authentication-conditional-access) をご覧ください。

![特定の外部組織から、多要素認証、コンプライアンス、ハイブリッドAzure ADに参加したデバイスを信頼する。](./cross-tenant-access-setting-ga/cross-tenant-access-setting-ga1.png)

## ユーザーが承認した外部組織とのみコラボレートするようにする 

アプリやリソースを外部からの不正アクセスから保護することが重要であるのと同様に、ユーザーが承認した組織としかコラボレーションしていないことを確認することも重要な場合があります。例えば、規制の強い業界に属し、データの流出について非常に敏感になっている組織があげられます。教育機関では、学生が学校のアカウントを使用して、許可されていない外部組織と Teams 上でチャットしている可能性もあります。このようなシナリオでは、ユーザーが未承認の外部テナントにアクセスするのをブロックする、送信方向のクロス テナント アクセス設定を導入することができます。教育業界のあるお客様は、ポリシーのテストと導入に 5 分もかからなかったそうです。これによりシンプルなセキュリティが実現できます。

詳細は [送信アクセス設定を変更する](https://docs.microsoft.com/ja-jp/azure/active-directory/external-identities/cross-tenant-access-settings-b2b-collaboration#modify-outbound-access-settings) ご覧ください。

![ユーザーのグループをターゲットにして、特定の組織への送信アクセスをブロックする。](./cross-tenant-access-setting-ga/cross-tenant-access-setting-ga2.png)

![同じグループのユーザーが、送信アクセス時に、どのアプリケーションにもアクセスできないようにブロックする。](./cross-tenant-access-setting-ga/cross-tenant-access-setting-ga3.png)

## Teams の共有チャンネルでシームレスなコラボレーションを実現 

Teams や SharePoint 上で、外部ユーザーとのコラボレーションを主に行っている場合、[Teams 共有チャネル](https://docs.microsoft.com/ja-jp/MicrosoftTeams/shared-channels) にて、複数の組織のユーザーと同時にチャットやファイル共有、コラボレーションを行うことができるシームレスなコラボレーションが可能です。上記で説明した受信および送信方向のクロス テナント アクセス ポリシーは、Teams 共有チャネルの [B2B 直接接続](https://docs.microsoft.com/ja-jp/azure/active-directory/external-identities/b2b-direct-connect-overview) ユーザーにも適用されます。 

![共有チャネルは、ユーザーがテナントを切り替えることなく、シームレスなコラボレーションを実現する。](./cross-tenant-access-setting-ga/cross-tenant-access-setting-ga4.png)

## お客様の声

パブリック プレビュー期間中、多くのお客様が上記の機能を試され、次のような感想を述べられています。 

> "クロス テナント アクセス設定は、外部組織とのコラボレーションを確保するために必要なコントロールを提供し、自社の保有財産を超えた「ゼロ トラスト」の道のりをサポートしてくれます。"  
> -- 保険業界のお客様からの声

> "Azure AD B2B により、当社のビジネスとパートナーや顧客との連携、サービスや製品へのアクセスを提供する方法が変革されました。クロス テナント アクセス設定は、より詳細で相互に合意可能なレベルの制御を実装する機能を提供することで、ビジネスを次のレベルへと押し上げました。これは多くのお客様からの重要な要望であり、両者が妥協することなく、データ保護要件を満たすために必要な制御を実施することが可能になります。"  
> -- プロフェッショナルサービス業界のお客様からの声

> "これらの機能により、セキュリティ管理が強化されるとともに、管理されたエンドポイント デバイスから外部テナントへのログインを強制できるようになるため、クロス テナント アクセスに非常に期待しています。クロス テナント アクセスは、リスクを大幅に削減し、セキュリティを向上させ、外部テナントへのアクセスやコラボレーションのニーズに関して、ビジネスをより良くサポートするのに役立っています。セキュリティ部門、ビジネス、そして重要なことですが、監査役や規制当局もこの機能に満足しています。"  
> -- 金融サービス業界のお客様 

## これはほんの始まりに過ぎません... 

みなさまもぜひクロス テナント アクセス設定をお使いいただければと思います。この設定を始める前に、外部組織とのコラボレーションを評価し、必要なコラボレーションを不注意で阻害することがないように、この [ワークブック](https://docs.microsoft.com/ja-jp/azure/active-directory/reports-monitoring/workbook-cross-tenant-access-activity) を活用ください。受信および送信方向のコラボレーション状況を把握できるよう、シンプルに構成されています。
 
この製品をどのように使用しているか、または今後どのようにすればより良くなるかについてのフィードバックをお待ちしています。Azure フォーラムや Twitter の @AzureAD タグでフィードバックを共有ください。 

Robin & Josh
Twitter: RobinGo_MS, @joshkdouglas

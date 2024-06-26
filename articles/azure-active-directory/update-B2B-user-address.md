---
title: Azure AD B2B ゲスト ユーザーの連絡先情報の更新方法について
date: 2023-04-07 06:00
tags:
  - Azure AD B2B
---

# Azure AD B2B ゲスト ユーザーの連絡先情報の更新方法について

> [!NOTE]
> 2020-10-22: 本記事の初版を投稿
> 2023-04-07: ポータル上の画面が変更されたことに伴い新しい画面ショットの案内を追記し更新

こんにちは、Azure Identity サポート チームの小田です。

今回は、Azure AD B2B ゲストユーザーの連絡先情報（電子メール / 連絡用メールアドレス）の更新方法についてご案内いたします。

Azure AD テナントにて別組織のユーザーを招待しますと、テナントにゲスト ユーザーが作成されます。ゲスト ユーザーの連絡先情報（電子メール / 連絡用メールアドレス）には、招待したときに指定した E メール アドレスが設定され、これらは Azure 側からの通知メール (計画メンテナンスなど) の宛先として使用されます。

ゲスト ユーザーが招待を承諾した後で、そのユーザーの実体が登録されているホーム テナント側で E メール アドレスの変更があった場合、そのユーザーをゲストとして登録しているリソース テナント側では、E メール アドレスの変更は反映されません。

そのため、ゲスト ユーザーがホーム テナント側で持っている属性値 (E メール アドレス等) を修正する場合、これまではゲスト ユーザーを一旦削除して「再招待」を実施するか、Microsoft Graph API、Exchange 管理センター、または Exchange Online PowerShell 経由で更新する必要がありました。

しかしながら、2020 年 10 月現在、ゲスト ユーザーの連絡先情報（電子メール / 連絡用メールアドレス）は、Azure AD 管理センターにて編集可能になりました。再招待を実施することなく、ゲスト ユーザーのメール アドレスの変更を変更する具体的な手順は、下記のとおりです。

## 変更手順

1. Azure ポータル [(https://portal.azure.com/)](https://portal.azure.com/) にアクセスし、グローバル管理者もしくはユーザー管理者にてサインインします。
2. [Azure Active Directory] - [ユーザー] - [すべてのユーザー] - [編集対象のゲストユーザー] をクリックし、[プロパティ] を開きます。
3. [編集] をクリックし、「連絡先情報」を編集します。

![](./update-B2B-user-address/address-update-in-AzurePortal.png)

4. [保存] をクリックします。

## 変更手順 (新しいプレビュー画面の場合)

Azure ポータルでは現在、ユーザーの画面については新しいプレビュー画面を利用可能です。新しい画面を利用している場合は、下記手順をご利用ください。

なお、従来の画面の "電子メール" は新しい画面の "メール" の項目に該当し、 "連絡用メール アドレス" は "その他のメール" の項目が該当します。

1. Azure ポータル [(https://portal.azure.com/)](https://portal.azure.com/) にアクセスし、グローバル管理者もしくはユーザー管理者にてサインインします。
2. [Azure Active Directory] - [ユーザー] - [すべてのユーザー] - [編集対象のゲストユーザー] をクリックし、[プロパティ] を開きます。
3. [編集] をクリックし、「連絡先情報」のタブを開きます。"メール" および "その他のメール"を編集します。

![](./update-B2B-user-address/address-update-in-aad2.png)

4. [保存] をクリックします。

## 参考情報

Azure Active Directory B2B コラボレーション ユーザーのプロパティ  
https://docs.microsoft.com/ja-jp/azure/active-directory/external-identities/user-properties#can-i-update-a-guest-users-email-address

Changelog for Microsoft Graph  
https://docs.microsoft.com/en-us/graph/changelog

なお、Azure ポータルでは、ゲスト ユーザーだけではなく、組織内ユーザーに対しても E メール アドレスを変更することが可能です。組織内のユーザーは、Exchange Online のライセンスが割り当たっている可能性もありますので、このような場合は、 Exchange Online 側で E メールアドレス操作を実施ください。

上記内容が少しでも参考となりますと幸いです。

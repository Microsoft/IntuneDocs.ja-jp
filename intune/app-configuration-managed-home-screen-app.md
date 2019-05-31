---
title: Microsoft Managed Home Screen アプリを構成する
titleSuffix: Microsoft Intune
description: Microsoft Managed Home Screen アプリの構成方法を学習します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/01/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 865c7f03-f525-4dfa-b3a8-d088a9106502
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b17ab1fb385bb1079a834f0a6fa690223ab64163
ms.sourcegitcommit: 01117021dfaebb5507aa146b7369447c3d5a403d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65626504"
---
# <a name="configure-the-microsoft-managed-home-screen-app-for-android-enterprise"></a>Android Enterprise 用 Microsoft Managed Home Screen アプリを構成する

Managed Home Screen は、Intune 経由で登録され、マルチアプリ キオスク モードで実行されている企業所有の Android エンタープライズ専用デバイスで使用するためのアプリケーションです。 これらのデバイスでは、Managed Home Screen は、その上で他の承認済みのアプリを実行するためのランチャーとして機能します。 Managed Home Screen では、IT 管理者がデバイスをカスタマイズして、エンド ユーザーがアクセスできる機能を制限する機能が提供されています。 

## <a name="when-to-configure-the-microsoft-managed-home-screen-app"></a>Microsoft Managed Home Screen アプリを構成するタイミング

通常、デバイス構成から設定が使用できる場合は、ここで設定を構成します。 これにより時間が節約され、エラーを最小限にし、Intune サポート エクスペリエンスの向上が可能になります。 ただし、Managed Home Screen の設定の中には、現在、Intune コンソールの **[アプリ構成ポリシー]** ブレードでしか使用できないものがあります。 このドキュメントを使用して、構成デザイナーまたは JSON スクリプトのいずれかを使用して、さまざまな設定を構成する方法について学習します。 

> [!NOTE]
> 現在可能でお勧めできるのは、**クライアント アプリ**と**デバイス構成**を使用して、ホワイトリストに登録されたアプリケーションを設定して、Web リンクをピン留めすることです。 Managed Home Screen に影響を与える**デバイス構成**で使用可能な設定の完全なリストについては、「[専用のデバイス設定](device-restrictions-android-for-work.md#dedicated-device-settings)」を参照してください。  

最初に、Azure portal で Intune コンソールに移動して、 **[クライアント アプリ]**  >  **[アプリ構成ポリシー]** の順に移動します。 **Android** を実行している**マネージド デバイス**に構成ポリシーを追加し、関連付けられているアプリとして **[Managed Home Screen]** を選択します。 **[構成設定]** をクリックして、利用可能なさまざまな Managed Home Screen 設定を構成します。 

## <a name="choosing-a-configuration-settings-format"></a>構成設定の形式を選択する

Managed Home Screen の構成設定を定義するのに使用できる 2 つの方法があります。

- **構成デザイナー**は、機能のオン/オフを切り替えたり、値を設定できる使いやすい UI を使用して設定を構成することができます。 この方法では、値の型 `BundleArray` で無効になるいくつかの構成キーがあります。 これらの構成キーは、JSON データを入力することによってのみ構成できます。 
- **JSON データ**を使用すると、JSON スクリプトを使用してすべての可能な構成キーを定義することができます。 

構成デザイナーでプロパティを追加する場合、 **[構成設定の形式]** ドロップダウンから **[JSON データを入力]** を選択することで、これらのプロパティを自動的に JSON に変換できます。

![構成設定の形式オプションのスクリーンショット](./media/app-configuration-managed-home-screen-app/app-configuration-managed-home-screen-app_01.png)

## <a name="using-configuration-designer"></a>構成デザイナーを使用する

構成デザイナーを使用すると、あらかじめ設定されている設定とそれらに関連付けられている値を選択できます。 

![追加された構成設定のスクリーンショット](./media/app-configuration-managed-home-screen-app/app-configuration-managed-home-screen-app_02.png)

次の表に、Managed Home Screen の使用可能な構成キー、値の型、既定値、および説明を示します。 説明では、選択した値に基づいて予想されるデバイスの動作を説明します。 構成デザイナーで無効になっている構成キーは、この表には含まれていません。

| 構成キー | 値の種類 | 既定値 | 説明 |
|---------------------------------------------------------------------------------------------------------------------------|-------------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| グリッド サイズの設定 | string | 自動 | Managed Home Screen に配置するアプリのグリッド サイズを設定できます。 アプリの行と列の数を設定して、`rows;column` の形式でグリッド サイズを定義することができます。 グリッド サイズを定義すると、設定した行数がホーム画面の 1 行に表示されるアプリの最大数になり、設定した列数がホーム画面の 1 列に表示されるアプリの最大数になります。 |
| スクリーン ヘッダーの有効化 | ブール | TRUE | Managed Home Screen で提供されるさまざまなビュー (フィードまたはフィード カードなど) の上部のヘッダーを有効にします。 この設定を有効にすると、デバイスのユーザーにヘッダーが表示されます。 |
| デバイスのステータス バーの有効化 | ブール | TRUE | ホーム画面でステータス バー (WiFi など現在の接続を表示する上部のバー) を有効にします。 この構成キーを有効にすると、エンド ユーザーが接続とアクティブなアプリを表すアイコンをステータス バーに表示できるようになります。 |
| 通知バッジの有効化 | ブール | FALSE | アプリ アイコンの通知バッジを有効にして、 アプリでの新しい通知の数を示します。 この設定を有効にすると、エンド ユーザーに未読の通知があることを知らせる通知バッジがアプリに表示されます。 この構成キーを無効のままにすると、未読の通知があっても、エンド ユーザーに知らせる通知バッジがアプリに表示されなくなります。 |
| ホーム画面のロック | ブール | TRUE | ホーム画面上のアプリ アイコンをエンド ユーザーが移動できないようにします。 この構成キーを有効にすると、ホーム画面上のアプリ アイコンがロックされ、エンド ユーザーがホーム画面の別のグリッドの位置にドラッグ アンド ドロップできなくなります。 `false` にすると、エンド ユーザーが Managed Home Screen 上のアプリケーションと Web リンクのアイコンを移動できるようになります。  |
| デバイスの壁紙の設定 | string | 既定 | 壁紙として設定する画像の URL を入力して、好みの壁紙を設定することができます。 |
| アプリ アイコンのサイズの設定 | integer | 2 | ホーム画面に表示されるアプリのアイコンのサイズを設定することができます。 この構成では、サイズごとに次の値を選択できます - 0 (最小)、1 (小)、2 (標準)、3 (大)、4 (最大)。 |
| アプリ フォルダー アイコンの設定 | integer | 0 | ホーム画面上のアプリ フォルダーの外観を定義することができます。 外観は、次の値から選択できます:濃色の正方形 (0)、濃色の円 (1)、淡色の正方形 (2)、淡色の円 (3)。 |
| ジェスチャを有効にする | ブール | FALSE | エンド ユーザーが、アクションをさまざまなジェスチャ (上方向にスワイプや下方向にスワイプなど) に割り当てられるようにします。 この構成キーを無効にした場合、エンド ユーザーは、2 番目のページがある場合に右へスワイプしてホーム ページに戻ることしかできなくなります。 |
| 垂直方向のスクロールの有効化 | ブール | FALSE | Managed Home Screen で垂直方向のスクロールを有効にします。 この構成キーを有効にすると、エンド ユーザーが別のページに移動する際に、水平方向ではなく、垂直方向にしかスワイプできなくなります。 |
| ホーム画面のテーマの設定 | string | Theme.Light.Blue | さまざまな色の定義済みのテーマのセットから、ホーム画面のテーマを選択することができます。 次のテーマを選択するには、次の形式で文字列値を入力します。   Theme.Light.Green。 Light を Dark に置き換えて濃色のテーマにすることも、Green (緑) を Blue (青)、Yellow (黄)、Pink (ピンク)、Red (赤)、Orange (オレンジ)、Purple (紫) に置き換えることもできます。 |
| ドッキングの有効化 | ブール | FALSE | ホーム画面の下部にあるアプリ ドック セクションを有効にして、固定アプリを表示し、インストールされているすべてのアプリのエントリ ポイントを表示します。 この構成キーを有効にすると、エンド ユーザーは、ホワイトリストに登録されているかどうかに関わらず、ドック内のアプリのほか、すべてのアプリ セクションにアクセスして、デバイスにインストールされているすべてのアプリのリストに移動することができます。 |
| 画面の向きの設定 | integer | 1 | ホーム画面の向きを縦モード、横モード、または自動回転に設定することができます。 向きを設定するには、値 1 (縦モード)、2 (横モード)、3 (自動回転) を入力します。 |
| ホーム画面フィードの有効化 | ブール | FALSE | ホーム画面を左にスワイプすると見られる、ホーム画面のフィードを有効にします。 このフィードには、ニュース、予定表、よく使われるアプリ、Cortana 音声アシスタント カードなどのさまざまなコンテンツの種類が表示されます。これを有効にすると、エンド ユーザーは、ホーム画面を左にスワイプしてフィードに移動できるようになります。 |
| 概要モードの有効化 | ブール | FALSE | 既定の画面から右にスワイプしてアクセスできるホーム画面に、エンド ユーザーがさまざまなページを追加または削除できるようにします。 これを有効にすると、エンド ユーザーはホーム画面の既定のページの右側にページを追加できるようになります。また、既定のページを変更したり、Managed Home Screen の設定にアクセスすることもできるようになります。 |
| デバイス テレメトリの有効化 | ブール | FALSE | Managed Home Screen 用にキャプチャされるすべてのテレメトリを有効にします。 これを有効にすると、このデバイスで特定のアプリが起動された回数など、Microsoft がデバイスの使用状況のテレメトリをキャプチャできるようになります。 |
| ホワイトリストに登録されたアプリケーションの設定 | bundleArray | FALSE | デバイスにインストールされているアプリの中からホーム画面に表示するアプリのセットを定義することができます。 表示したいアプリのパッケージ名を入力することでアプリを定義できます。たとえば、"com.android.settings" と入力すると、設定がホーム画面でアクセスできるようになります。 このセクションでホワイトリストに登録するアプリをホーム画面に表示するには、アプリが既にインストールされている必要があります。 |
| ピン留めされた Web リンクの設定 | bundleArray | FALSE | Web サイトをクイック起動アイコンとしてホーム画面にピン留めすることができます。 この構成では、エンド ユーザーがブラウザー内で 1 回のタップで起動できるように、URL を定義して、それをホーム画面に追加することができます。 |
| 検索バーの有効化 | ブール | FALSE | ホーム画面で検索バーを有効にします。 これを有効にすると、デバイスのユーザーのホーム画面に検索バーが表示されるようになり、ユーザーが Web で検索したいことを入力することができます。 |
| 設定アプリの無効化 | ブール | FALSE | Managed Home Screen の設定ページを無効にします。 これを無効にすると、デバイスのエンド ユーザーが、Managed Home Screen の設定ページにアクセスできなくなります。 |
| スクリーン セーバーを有効にする | ブール | FALSE | スクリーンセーバー モードを有効または無効にします。 true に設定すると、**screen_saver_image**、**screen_saver_show_time**、**inactive_time_to_show_screen_saver**、**media_detect_screen_saver** を構成できます。 |
| スクリーン セーバーの画像 | string |   | スクリーンセーバーの画像の URL を設定します。 URL が設定されていない場合、スクリーンセーバーがアクティブになると、デバイスには既定のスクリーンが表示されます。  |
| スクリーン セーバーの表示時間 | integer | 0 | スクリーンセーバー モード時にデバイスでスクリーンセーバーが表示される時間を秒単位で設定するオプションを提供します。 0 に設定すると、スクリーンセーバー モードではスクリーンセーバーが、デバイスがアクティブになるまで無期限に表示されます。  |
| スクリーン セーバーが有効になるまでの非アクティブ状態の時間 | integer | 30 | スクリーンセーバーをトリガーするまでにデバイスが非アクティブな状態の秒数。 0 に設定すると、デバイスはスクリーンセーバー モードになりません。 |
| スクリーン セーバーを表示する前のメディアの検出 | ブール | TRUE | デバイスでオーディオ/ビデオが再生されている場合に、デバイスの画面にスクリーンセーバーを表示するかどうかを選択します。 true に設定すると、**inactive_time_to_show_scree_saver** の値に関係なく、デバイスでオーディオ/ビデオが再生されなくなります。 false に設定すると、**inactive_time_to_show_screen_saver** に設定されている値に従って、デバイスの画面でスクリーンセーバーが表示されます。   |
| 仮想ホーム ボタンの有効化 | ブール | FALSE | エンド ユーザーに Managed Home Screen のホーム ボタンへのアクセスを許可するには、この設定を `True` にします。このボタンを使用すると、ユーザーが現在行っているタスクから Managed Home Screen へ戻ることができます。  |
| 仮想ホーム ボタンの種類 | string | Swipe_up | 上方向にスワイプのジェスチャでホーム ボタンにアクセスするには、**swipe_up** を使用します。 エンド ユーザーが画面を移動できる固定の永続的なホーム ボタンにアクセスするには、**float** を使用します。 |
| バッテリと信号の強さのインジケーター バー | ブール | True  | この設定を `True` にすると、バッテリと信号の強さのインジケーター バーが表示されます。 |
| ロック タスク モード終了のパスワード | string |   | トラブルシューティングのためにロック タスク モードを一時的に停止するために使用する 4 - 6 桁のコードを入力します。 |
| Wi-Fi 設定の表示 | ブール | FALSE | この設定を `True` にすると、エンド ユーザーが Wi-Fi をオン/オフにしたり、別の Wi-Fi ネットワークに接続できるようになります。  |
| Bluetooth の設定の表示 | ブール | FALSE | この設定を `True` にすると、エンド ユーザーが Bluetooth をオン/オフにしたり、別の Bluetooth 対応デバイスに接続できるようになります。   |

## <a name="enter-json-data"></a>JSON データの入力

JSON データを入力して、Managed Home Screen で使用可能なすべての設定と、**構成デザイナー**しで無効にされた設定を構成します。

![追加された JSON データのスクリーンショット](./media/app-configuration-managed-home-screen-app/app-configuration-managed-home-screen-app_03.png)

**構成デザイナー**の表 (上) に一覧表示されている構成可能な設定のリストに加え、次の表では、JSON データを使用してのみ構成できる構成キーを示します。

|    構成キー    |    値の型    |    既定値    |    説明    |
|-------------------------------------------------|--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    ホワイトリストに登録されたアプリケーションの設定    |    bundleArray    | ``` json   {        "key":   "applications",        "valueBundleArray": [        {                                    "managedProperty": [   {         "key": "package",         "valueString":   STRING_VALUE   }   ]        }        ]   },   ``` |    デバイスにインストールされているアプリの中からホーム画面に表示するアプリのセットを定義することができます。 表示したいアプリのパッケージ名を入力することでアプリを定義できます。たとえば、"com.android.settings" と入力すると、設定がホーム画面でアクセスできるようになります。 このセクションでホワイトリストに登録するアプリをホーム画面に表示するには、アプリが既にインストールされている必要があります。    |
|    ピン留めされた Web リンクの設定    |    bundleArray    | ``` json   {        "key": "weblinks",        "valueBundleArray": [         {               "managedProperty": [     {          "key": "link",          "valueString":   STRING_VALUE      },      {           "key": "label",           "valueString": STRING_VALUE      }      ]         }         ]   },   ``` |    Web サイトをクイック起動アイコンとしてホーム画面にピン留めすることができます。 この構成では、エンド ユーザーがブラウザー内で 1 回のタップで起動できるように、URL を定義して、それをホーム画面に追加することができます。    |
|    アプリをグループ化するためのマネージド フォルダーの作成    |    bundleArray    | ``` json   {        "key": “managed_folders",        "valueBundleArray": [         {               "managedProperty": [     {            "key": "folder_name",            "valueString": STRING_VALUE      },      {             "key": "content",                      "valueBundleArray":   [                        {                             "managedProperty": [                    {                              “key”: “type”,                             “valueString”: STRING_VALUE                    },                    {                              “key”: “label”,                             “valueString”: STRING_VALUE                    },                    {                              “key”: “package”,                             “valueString”: STRING_VALUE                    },                    {                              “key”: “class”,                             “valueString”: STRING_VALUE                    },                    {                              “key”: “link”,                             “valueString”: STRING_VALUE                    }                 ]              }          ]      }              ]          }      ]   },   ``` |    フォルダーを作成し、名前を付けて、これらのフォルダー内にアプリをグループ化することができます。 エンド ユーザーはフォルダーを移動したり、フォルダーの名前を変更したり、フォルダー内でアプリを移動したりすることができなくなります。   フォルダーは作成された順に表示され、フォルダー内のアプリはアルファベット順に表示されます。         注: フォルダーにグループ化するすべてのアプリは、必要に応じてデバイスに割り当てる必要があり、また Managed Home Screen に追加されている必要があります。     |

以下は、使用可能なすべての構成キーが含まれた JSON スクリプトの例です。

```json
{
    "kind": "androidenterprise#managedConfiguration",
    "productId": "com.microsoft.launcher.enterprise",
    "managedProperty": [
        {
            "key": "grid_size",
            "valueString": "Auto"
        },
        {
            "key": "keep_page_header",
            "valueBool": true
        },
        {
            "key": "keep_status_bar",
            "valueBool": true
        },
        {
            "key": "show_notification_badge",
            "valueBool": false
        },
        {
            "key": "lock_home_screen",
            "valueBool": true
        },
        {
            "key": "wallpaper",
            "valueString": "default"
        },
        {
            "key": "icon_size",
            "valueInteger": 2
        },
        {
            "key": "app_folder_icon",
            "valueInteger": 0
        },
        {
            "key": "gesture_on",
            "valueBool": false
        },
        {
            "key": "vertical_scrolling",
            "valueBool": false
        },
        {
            "key": "theme",
            "valueString": "Theme.Light.Blue"
        },
        {
            "key": "dock_enable",
            "valueBool": false
        },
        {
            "key": "screen_orientation",
            "valueInteger": 1
        },
        {
            "key": "feed_enable",
            "valueBool": false
        },
        {
            "key": "allow_overview_mode",
            "valueBool": false
        },
        {
            "key": "enable_telemetry",
            "valueBool": false
        },
        {
            "key": "applications",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "package",
                            "valueString": “app package name here”
                        }
                    ]
                }
            ]
        },
        {
            "key": "weblinks",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "link",
                            "valueString": “link here”
                        },
                        {
                            "key": "label",
                            "valueString": “weblink label here”
                        }
                    ]
                }
            ]
        },
        {
            "key": "search_bar",
            "valueBool": false
        },
        {
            "key": "hide_settings",
            "valueBool": false
        },
        {
            "key": "show_virtual_home",
            "valueBool": false
        },
        {
            "key": "virtual_home_type",
            "valueString": "swipe_up"
        },
        {
            "key": "show_virtual_status_bar",
            "valueBool": true
        },
        {
            "key": "exit_lock_task_mode_code",
            "valueString": ""
        },
        {
            "key": "show_wifi_setting",
            "valueBool": false
        },
        {
            "key": "show_bluetooth_setting",
            "valueBool": false
        },
        {
            "key": "managed_folders",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "folder_name",
                            "valueString": "Folder name here"
                        },
                        {
                            "key": "applications",
                            "valueBundleArray": [
                                {
                                    "managedProperty": [
                                        {
                                            "key": "package",
                                            "valueString": "com.microsoft.emmx"
                                        }
                                    ]
                                },
                                {
                                    "managedProperty": [
                                        {
                                            "key": "package",
                                            "valueString": "com.microsoft.bing"
                                        }
                                    ]
                                },
                                {
                                    "managedProperty": [
                                        {
                                            "key": "link",
                                            "valueString": "https://microsoft.com/"
                                        }
                                    ]
                                }
                            ]
                        }
                    ]
                },
                {
                    "managedProperty": [
                        {
                            "key": "folder_name",
                            "valueString": "Example folder name 2"
                        },
                        {
                            "key": "applications",
                            "valueBundleArray": [
                                {
                                    "managedProperty": [
                                        {
                                            "key": "package",
                                            "valueString": "com.microsoft.office.word"
                                        }
                                    ]
                                }
                            ]
                        }
                    ]
                }
            ]
        }
    ]
}

```
## <a name="next-steps"></a>次の手順

- Android エンタープライズ専用デバイスの詳細については、「[Android エンタープライズ専用デバイスの Intune 登録を設定する](android-kiosk-enroll.md)」を参照してください。

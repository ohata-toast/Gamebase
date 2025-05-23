## Game > Gamebase > Unreal SDK使用ガイド > 開始する

Gamebase Unreal SDKの使用環境および初期設定の説明を行います。

## Environments

> [参考] 
>
> Unrealサポートバージョン
>
> * UE 4.27~UE 5.4
> * 他のバージョンのサポートが必要な場合は[サポート](https://toast.com/support/inquiry)へお問い合わせください。

#### Supported Platforms

* Android
* iOS
* Windows

選択したプラットフォームでサポートしないGamebase APIを呼び出す時は、下記のエラーがコールバックで返り、コールバックがない場合はWarningログが出力されます。

* GamebaseErrorCode::NOT_SUPPORTED
* GamebaseErrorCode::NOT_SUPPORTED_ANDROID
* GamebaseErrorCode::NOT_SUPPORTED_IOS
* GamebaseErrorCode::NOT_SUPPORTED_UE_STANDALONE
* GamebaseErrorCode::NOT_SUPPORTED_UE_EDITOR

各APIでサポートするプラットフォームは、下記のアイコンで区別します。

**API**

Supported Platforms
<span style="color:#0E8A16; font-size: 10pt">■</span> UNREAL_ANDROID
<span style="color:#1D76DB; font-size: 10pt">■</span> UNREAL_IOS
<span style="color:#F9D0C4; font-size: 10pt">■</span> UNREAL_WINDOWS

## Installation

1. Gamebase Unreal SDKをダウンロードして、プロジェクトパスに`Plugins`フォルダを作成し、ダウンロードしたSDK内部 **NHNCloud**フォルダを追加します。
2. Unrealエディタで`Settings > Plugins`ウィンドウを開き、`Project > NHN Cloud > Gamebase Plugin`プラグインを探して有効にします。

* [Download Gamebase Unreal SDK](/Download/#game-gamebase)

### Module Settings

* Gamebaseコードを使用するには、モジュールのBuild.csファイルの依存モジュール設定時に、下記のようにモジュールを追加する必要があります。

        PrivateDependencyModuleNames.AddRange(
            new[]
            {
                "Gamebase",
            }
        );

### Android Settings

1. エディタのメニュー **Edit > Project Settings**を選択します。
2. Project SettingsウィンドウでPluginカテゴリーから**Gamebase**を選択します。

![Unreal Project Settings - Android](https://static.toastoven.net/prod_gamebase/UnrealDevelopersGuide/unreal-developers-guide-started-android-settings-2.63.0.png)

* Android - Authentication
    * 使用するIdPを有効にします。
    * Hangame IdPを使用する時は、サポートへお問い合わせください。
    * GPGS(Google Play Games Services)
        * Auto Login - GPGS自動ログインをサポート  
* Push
    * 使用したいプッシュサービスを有効にします。
    * FCM
        * 該当機能を使用する場合に有効になります。
        * GoogleServicesFilePath - [Firebase Notification Settings](./aos-started/#firebase-notification)でダウンロードしたgoogle-services.jsonファイルのパスを指定します。
* Purchase
    * 使用するストアを選択します。
    * ONE Store
        * 該当ストアを使用する場合に有効化になります。
        * View Option - 全体決済画面(Full)とポップアップ決済画面(Popup)のいずれかを選択します。

#### Google Play認証および決済ができない問題

Google Playサービスに認証と決済を行うには、Distributionの設定が必要です。
詳細な内容は、以下の文書を参照してください。 

* [Signing Projects for Release](https://docs.unrealengine.com/en-US/Platforms/Mobile/Android/DistributionSigning/index.html)

#### GPGS(Google Play Games Services)設定

Sign in with Apple使用時、プロジェクトで/Config/Android/AndroidEngine.iniファイルに下記の内容を追加してGPGSのApplication IDを入力します。

```ini
[/Script/AndroidRuntimeSettings.AndroidRuntimeSettings]
GamesAppID=
```

#### AndroidX適用

* Gamebase Android SDK 2.25.0からAndroidXが導入され、[UPL(Unreal Plugin Language)](https://docs.unrealengine.com/4.27/en-US/SharingAndReleasing/Mobile/UnrealPluginLanguage/)ファイルの下に設定を追加する必要があります。

```xml
<gradleProperties>    
  <insert>
    android.useAndroidX=true      
    android.enableJetifier=true    
  </insert>  
</gradleProperties>
```

#### multidex適用

* Gamebase Unreal SDK 2.26.0からGamebase内部で設定したmultidex関連内容が削除されたため、[UPL(Unreal Plugin Language)](https://docs.unrealengine.com/4.27/en-US/SharingAndReleasing/Mobile/UnrealPluginLanguage/)ファイルに以下の設定を追加する必要があります。

```xml
<buildGradleAdditions>
  <insert>
  android {
    defaultConfig {
      multiDexEnabled true
    }
  }
  </insert>
</buildGradleAdditions>

<androidManifestUpdates>
    <addAttribute tag="application" name="android:name" value="androidx.multidex.MultiDexApplication"/>
</androidManifestUpdates>
```

### iOS Settings

Gamebase SDK for Unrealを使用するには`UE4 Githubソースコード`を使用する必要があり、Epic gamesに会員登録した後、Githubアカウントを接続するとUnrealEngine repositoryが表示されます。
See below for relevant guides. 

* [Downloading Unreal Engine Source Code](https://docs.unrealengine.com/5.0/en-US/downloading-unreal-engine-source-code/)
* [Getting up and running](https://github.com/EpicGames/UnrealEngine#getting-up-and-running)

>`!重要`
> このプロセスを無視すると、以下のガイドリンクが正常に動作しなかったりGamebase SDK for Unrealを使用できません。

#### Project Settings

1. エディタのメニュー**Edit > Project Settings**を選択します。
2. Project SettingsウィンドウでPluginカテゴリーから**Gamebase - iOS**を選択します。

![Unreal Project Settings - iOS](https://static.toastoven.net/prod_gamebase/UnrealDevelopersGuide/unreal-developers-guide-started-ios-setttings-2.57.0.png)

* Path
    * Xcode Path：Xcodeのパスを入力します。 (デフォルト値： /Applications/Xcode.app)

* Authentication
    * 使用したいIdPを有効にします。
* Purchase
    * 使用したいストアを選択します。
* Push
    * 使用したいプッシュサービスを有効にします。

#### Gamebase Unreal SDKを使用するためのエンジン変更

Gamebase Unreal SDK及び外部認証SDKでswiftで開発されたフレームワークをコンパイルするには、[Engine/Source/Programs/UnrealBuildTool/Platform/IOS/IOSToolChain.cs](https://github.com/EpicGames/UnrealEngine/blob/4.26/Engine/Source/Programs/UnrealBuildTool/Platform/IOS/IOSToolChain.cs)ファイルで下記のコードを追加してください。

```cs
// need to tell where to load Framework dylibs
Result += " -rpath /usr/lib/swift";                 // 追加コード
Result += " -rpath @executable_path/Frameworks";
```

#### Sign in with Apple

Sign in with Appleを使う時、プロジェクトで /Config/IOS/IOSEngine.ini ファイルに下記の内容を追加します。

```ini
[/Script/IOSRuntimeSettings.IOSRuntimeSettings]
bEnableSignInWithAppleSupport=True
```

#### Remote Notification

1. Gamebase Remote Notification機能を使用するには、Project Settings > Platforms > iOSページでEnable Remote Notifications Support機能を有効化する必要があります。(Githubソースからのみ可能)
2. Foregroundプッシュ通知を受け取るには[Engine/Source/Runtime/ApplicationCore/Private/IOS/IOSAppDelegate.cpp](https://github.com/EpicGames/UnrealEngine/blob/4.26/Engine/Source/Runtime/ApplicationCore/Private/IOS/IOSAppDelegate.cpp)ファイルから以下のコードを削除するか

        - (void)userNotificationCenter:(UNUserNotificationCenter *)center
            willPresentNotification:(UNNotification *)notification
                withCompletionHandler:(void (^)(UNNotificationPresentationOptions options))completionHandler
        {
            // Received notification while app is in the foreground
            HandleReceivedNotification(notification);
        
            completionHandler(UNNotificationPresentationOptionNone);
        }

   次のように修正する必要があります。
        
            // AS-IS
            completionHandler(UNNotificationPresentationOptionNone);
            
            // TO-BE
            completionHandler(UNNotificationPresentationOptionAlert);

#### Rich Push Notification

次のようなイシューによりRich Push Notification機能を使用できません。

* Unrealはプロジェクトに[Notification Service Extension](https://developer.apple.com/documentation/usernotifications/unnotificationserviceextension?language=objc)を追加できる方法を提供しません。
    * [NHN Cloud Push Notification Service Extension作成](https://docs.toast.com/e  n/TOAST/en/toast-sdk/push-ios/#notification-service-extension)

#### iOS SDKのWarningメッセージによるUnrealビルドエラー

iOS SDKで発生するWarningメッセージがUnrealビルド時、エラーに変換されてビルドに失敗する現象が発生する場合は[Engine/Source/Programs/UnrealBuildTool/Platform/IOS/IOSToolChain.cs](https://github.com/EpicGames/UnrealEngine/blob/release/Engine/Source/Programs/UnrealBuildTool/Platform/IOS/IOSToolChain.cs)ファイルのclangコンパイルオプションコードをコメント処理してください。

```cs
// Result += " -Wall -Werror";
```

#### PLCrashReporter

UE4で使用中のPLCrashReporterが`arm64e` architectureをサポートしておらず、該当architectureを使用するデバイスでメモリアドレス値を取得できないイシューがあります。

NHN Cloud Log & Crash Searchでクラッシュ分析を行うゲーム開発会社は、次のガイドを参照してUE4内部PLCrashReporterを修正する必要があります。

1. GamebaseSDK-Unreal/Source/Gamebase/ThirdParty/IOS/plcrashreporter.zipファイルを解凍します。
2. UE4内部PLCrashReporterのaファイルとheaderファイルを解凍したファイルと交換します。
    * Engine/Source/ThirdParty/PLCrashReporter/plcrashreporter-master-xxxxxxx

### Windows Settings

1. エディタのメニュー **Edit > Project Settings**を選択します。
2. Project SettingsウィンドウでPluginカテゴリーから**Gamebase - Windows**を選択します。

![Unreal Project Settings - Windows](https://static.toastoven.net/prod_gamebase/UnrealDevelopersGuide/unreal-developers-guide-started-windows-setttings-2.57.0.png)

* Authentication
    * 使用する IdP を有効にします。
* Purchase
    * 使用したいストアを選択します。
    * Epic Games Store
        * EOSサービス情報を各項目に合わせて入力します。

#### WebViewプラグイン案内

* WebViewを使用するコンテンツを使用する場合、プラグインの有効化が必要です。
    * Login with IdP
        * GUEST以外のIdPをサポートする場合、WebViewでログイン処理を行います。
    * ImageNotices
    * WebView
* エンジンを修正せずにWebView関連機能を使用する場合、Unrealエディタで**Settings > Plugins**ウィンドウを開き、**Project > NHN Cloud > NHNWebView**プラグインを見つけて有効にします。
* エンジンが提供するWeb Browserプラグインを使用する場合、UE 5.4以上が必要であり、それ以下のバージョンではCEFのバージョンが低いため、Web Browserプラグインが正常に動作しないため、Web Browserプラグインと関連するモジュールのアップデートが必要です。
    * ThirdParty
        * CEF3
    * Runtime
        * CEF3Utils
        * WebBrowser
        * WebBrowserTexture
    * Program
        * EpicWebHelper

> [注意]
> NHNWebViewプラグインとWeb Browserプラグインは同時に使用することができず、両方のプラグインが有効になっている場合、ビルド時にエラーが発生します。

#### Epic Games Storeサービス

* UE 4.27以降のバージョンでサポートされ、エンジン内部にEOSSDKモジュールが使用されています。
* Epic Games Storeを使用するためには、EOSSDKを使用してログインする必要があります。
* Gamebase で使用する EOS のバージョンは 1.15.5.0 で、エンジンパス `Engine\Source\ThirdParty\EOSSDK\SDK` に該当バージョンをインストールしてアップグレードする必要があります。
    * [参考: EOS SDKアップグレードガイド](https://docs.unrealengine.com/5.2/en/upgrading-the-eos-sdk-in-unreal-engine/)
* ゲーム起動時にEOS Handleの設定が必要です。
    * エンジンに含まれているOnline Subsystem EOSを使用する場合、下記のコードのように設定できます。

            #include "OnlineSubsystemEOS.h"
            #include "IEOSSDKManager.h"
            #include "GamebaseStandalonePurchaseEpicAdapterModule.h"

            void UGamebasePurchaseEpicSupportTestCase::SetEosPlatformInstance()
            {
                IOnlineSubsystem* Subsystem = Online::GetSubsystem(GetWorld());

                if (const FOnlineSubsystemEOS* EosSubsystem = static_cast<FOnlineSubsystemEOS*>(Subsystem))
                {
                    EOS_HPlatform PlatformHandle = *EosSubsystem->EOSPlatformHandle;
                    FGamebaseStandalonePurchaseEpicModule::SetEosPlatformInstance(*Handle);
                }
            }

        > `OnlineSubsystemEOS.h`ヘッダーを含めるとビルドエラーが発生するので、OnlineSubsystemEOSプラグインのPrivateフォルダ内のHeaderファイルをPublicフォルダへ移動する必要があります。 (参考： [EOSエラーに関するお問い合わせ](https://eoshelp.epicgames.com/s/question/0D54z00007QIJjhCAH/cant-call-get-voice-chat-user-interface-from-game-instance-using-the-eos-plugin-and-eos-voice-plugins-on-unreal-engine4?language=en_US))
        > - SocketSubsystemEOS.h 
        > - EOSSettings.h
        > - EOSHelpers.h
        > - [Platform]/[Platform]EOSHelpers.h

#### Steamworksサービス

* WindowsでSteam認証と決済はSteamworks SDKを通じて行われます。
* Gamebaseで使用するSteamworksのバージョンは1.57以上です。 UE 5.3以下を使用する場合Steamworksをアップデートする必要があります。
    * Online Subsystem Steamを使用する場合、最新バージョンのOnline SubsystemとOnline Subsystem Steamの最新バージョン適用コードを参照してアップデートする必要があります。
        * [参考: Online Subsystem Steamエンジン最新バージョンコミット](https://github.com/EpicGames/UnrealEngine/commit/f6fd8dcf34a0cc31412dd473c1309c8e507981f3#diff-cd0b8c3bbdff4546195efef417923e90acead93b3625d8d82afe82fe0939b8a6)
    * Online Subsystem Steamを使用しない場合は、エンジンガイドを確認してSteamworks SDK 1.57バージョン以上をダウンロードし、エンジンのSteamworksモジュールをそのバージョンにアップデートしてください。
        * [参考:エンジン内Steamworksアップグレードガイド](https://dev.epicgames.com/documentation/en-us/unreal-engine?application_version=4.27)
* 内部では、Online Subsystem設定オプションのDefaultPlatformServiceの値がSteamの場合、自動的にOnline Subsystem Steamを使用しているものとみなされます。この値がない場合、エンジン内部にSteamworksモジュールのインストールバージョンを確認し、1.57以上の場合、Gamebase内のSteam機能が動作します。

> [注意]
> Online Subsystem Steamを使用せずにSteamworksのみを使用する場合、Gamebase内部でSteamworksを使用した認証情報を受け取る作業のみを行い、Steamworks SDKプロセスは行われません。
> Steamworks SDKを直接適用する場合、初期化、アップデート、終了などの必須的な処理については直接実装する必要があります。

## API Deprecate Governance

GamebaseでサポートしないAPIはDeprecate処理します。
DeprecatedされたAPIは、次の条件を満たすと、事前告知を行わずに削除される場合があります。

* 5回以上のマイナーバージョンアップデート
	* Gamebase Version Format - XX.YY.ZZ
		* XX : Major
		* YY : Minor
		* ZZ : Hotfix

* 5か月経過

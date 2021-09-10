---
title: Disinstallare Visual Studio per Mac
description: Istruzioni per la disinstallazione di Visual Studio per Mac e degli strumenti correlati.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.technology: vs-ide-install
ms.assetid: 4EB95F75-BC2E-4982-9564-2975805712D8
ms.topic: how-to
ms.openlocfilehash: 518dd80d230e3d2518ae69520781818826363ecc
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123964734"
---
# <a name="uninstalling-visual-studio-for-mac"></a>Disinstallazione di Visual Studio per Mac

È possibile usare questa guida per disinstallare ogni componente di Visual Studio per Mac passando alla sezione pertinente oppure usare gli script disponibili nella sezione [Script di disinstallazione](#uninstall-script) per disinstallare tutti i componenti.

> [!NOTE]
> Queste informazioni consentono di rimuovere dal computer solo Visual Studio 2019 o 2017 per Mac. Per disinstallare Visual Studio Code, vedere la soluzione a [questo problema](https://github.com/Microsoft/vscode/issues/52151).

## <a name="uninstall-script"></a>Script di disinstallazione

Sono disponibili due script per disinstallare Visual Studio per Mac e tutti i relativi componenti dal computer:

- [Script per Visual Studio e Xamarin](#visual-studio-for-mac-and-xamarin-script)
- [Script per .NET Core](#net-core-script)

Le sezioni seguenti offrono informazioni sul download e sull'uso degli script.

### <a name="visual-studio-for-mac-and-xamarin-script"></a>Script per Visual Studio per Mac e Xamarin

È possibile disinstallare contemporaneamente i componenti di Visual Studio e Xamarin usando lo [script di disinstallazione](https://raw.githubusercontent.com/MicrosoftDocs/visualstudio-docs/master/mac/resources/uninstall-vsmac.sh).

Questo script di disinstallazione contiene la maggior parte dei comandi che si trovano nell'articolo. Tre elementi principali sono stati omessi dallo script, a causa di possibili dipendenze esterne. Per rimuoverli, passare alla sezione pertinente di sotto e procedere manualmente:

- **[Disinstallazione di Mono](#uninstall-mono-sdk-mdk)**
- **[Disinstallazione di Android AVD](#uninstall-android-avd)**
- **[Disinstallazione di Android SDK e Java SDK](#uninstall-android-sdk-and-java-sdk)**

Per eseguire lo script, seguire questa procedura:

1. Fare clic con il pulsante destro del mouse sullo script e selezionare **Salva con nome** per salvare il file nel Mac.
2. Aprire Terminal e modificare la directory di lavoro in cui lo script è stato scaricato:

    ```bash
    cd /location/of/file
    ```

3. Rendere eseguibile lo script ed eseguirlo con **sudo**:

    ```bash
    chmod +x ./uninstall-vsmac.sh
    sudo ./uninstall-vsmac.sh
    ```

4. Infine, eliminare lo script di disinstallazione e rimuovere Visual Studio per Mac dal Dock (se presente).

### <a name="net-core-script"></a>Script per .NET Core

Lo script di disinstallazione di .NET Core si trova in [dotnet cli repo](https://raw.githubusercontent.com/dotnet/cli/master/scripts/obtain/uninstall/dotnet-uninstall-pkgs.sh)

Per eseguire lo script, seguire questa procedura:

1. Fare clic con il pulsante destro del mouse sullo script e selezionare **Salva con nome** per salvare il file nel Mac.
2. Aprire Terminal e modificare la directory di lavoro in cui lo script è stato scaricato:

    ```bash
    cd /location/of/file
    ```

3. Rendere eseguibile lo script ed eseguirlo con **sudo**:

    ```bash
    chmod +x ./dotnet-uninstall-pkgs.sh
    sudo ./dotnet-uninstall-pkgs.sh
    ```

4. Eliminare infine lo script di disinstallazione di .NET Core.

## <a name="uninstall-visual-studio-for-mac"></a>Disinstallare Visual Studio per Mac

Il primo passaggio nella disinstallazione di Visual Studio da un Mac consiste nell'individuare **Visual Studio.app** nella directory **/Applicazioni** e trascinarla nel **Cestino**. In alternativa, fare clic con il pulsante destro del mouse e scegliere **Sposta nel cestino** come illustrato nella figura seguente:

![Spostare l'applicazione Visual Studio nel cestino](media/uninstall-image1.png)

L'eliminazione di questo bundle dell'app causa la rimozione di Visual Studio per Mac, anche se è possibile che nel file system restino altri file associati a Xamarin.

Per rimuovere tutte le tracce di Visual Studio per Mac, eseguire i comandi seguenti in Terminal:

```bash
sudo rm -rf "/Applications/Visual Studio.app"
rm -rf ~/Library/Caches/VisualStudio
rm -rf ~/Library/Preferences/VisualStudio
rm -rf ~/Library/Preferences/Visual\ Studio
rm -rf ~/Library/Logs/VisualStudio
rm -rf ~/Library/VisualStudio
rm -rf ~/Library/Preferences/Xamarin/
rm -rf ~/Library/Application\ Support/VisualStudio
rm -rf ~/Library/Application\ Support/VisualStudio/7.0/LocalInstall/Addins/
rm -rf ~/Library/Application\ Support/VisualStudio/8.0/LocalInstall/Addins/
```

Può anche essere necessario rimuovere la directory seguente che contiene diversi file e cartelle di Xamarin. Tuttavia, prima di procedere è necessario tenere presente che questa directory contiene le chiavi di firma di Android. Per altre informazioni, vedere la sezione **[Disinstallazione di Android SDK e Java SDK](#uninstall-android-sdk-and-java-sdk)**:

```bash
rm -rf ~/Library/Developer/Xamarin
```

## <a name="uninstall-mono-sdk-mdk"></a>Disinstallare Mono SDK (MDK)

Mono è un'implementazione open source di Microsoft .NET Framework ed è usato da tutti i prodotti Xamarin (Xamarin.iOS, Xamarin.Android e Xamarin.Mac) per consentire lo sviluppo per queste piattaforme in C#.

> [!WARNING]
> Vi sono altre applicazioni al di fuori di Visual Studio per Mac che usano Mono, ad esempio Unity.
> Prima di disinstallare Mono, assicurarsi che non vi siano altre dipendenze.

Per rimuovere Mono Framework da un computer, eseguire i comandi in Terminal:

```bash
sudo rm -rf /Library/Frameworks/Mono.framework
sudo pkgutil --forget com.xamarin.mono-MDK.pkg
sudo rm -rf /etc/paths.d/mono-commands
```

## <a name="uninstall-xamarinandroid"></a>Disinstallare Xamarin.Android

Per l'installazione e l'uso di Xamarin.Android sono richiesti diversi elementi, ad esempio Android SDK e Java SDK.

Usare i comandi seguenti per rimuovere Xamarin.Android:

```bash
sudo rm -rf /Developer/MonoDroid
rm -rf ~/Library/MonoAndroid
sudo pkgutil --forget com.xamarin.android.pkg
sudo rm -rf /Library/Frameworks/Xamarin.Android.framework
```

### <a name="uninstall-android-sdk-and-java-sdk"></a>Disinstallare Android SDK e Java SDK

Android SDK è richiesto per lo sviluppo di applicazioni Android. Per rimuovere completamente tutte le parti di Android SDK, individuare il file in **~/Library/Developer/Xamarin/** e spostarlo nel **Cestino**.

> [!WARNING]
> È necessario tenere presente che le chiavi di firma Android generate da Visual Studio per Mac si trovano in `~/Library/Developer/Xamarin/Keystore`. Assicurarsi di eseguirne il backup in modo appropriato oppure evitare di rimuovere la directory se si vuole mantenere l'archivio chiavi.

Non è necessario disinstallare Java SDK (JDK) poiché è già inserito nel pacchetto come parte di Mac OS X / macOS.

### <a name="uninstall-android-avd"></a>Disinstallare Android AVD

> [!WARNING]
> Altre applicazioni oltre a Visual Studio per Mac usano Android AVD e questi componenti di Android aggiuntivi, quali Android Studio. La rimozione di questa directory può causare l'interruzione di progetti in Android Studio.

Per rimuovere tutti gli Android AVD e i componenti di Android aggiuntivi, usare il comando seguente:

```bash
rm -rf ~/.android
```

Per rimuovere solo gli Android AVD, usare il comando seguente:

```bash
rm -rf ~/.android/avd
```

## <a name="uninstall-xamarinios"></a>Disinstallare Xamarin.iOS

Xamarin.iOS consente di sviluppare applicazioni iOS usando C# o F# con Visual Studio per Mac.

Usare i comandi seguenti in Terminal per rimuovere tutti i file Xamarin.iOS da un file system:

```bash
rm -rf ~/Library/MonoTouch
sudo rm -rf /Library/Frameworks/Xamarin.iOS.framework
sudo rm -rf /Developer/MonoTouch
sudo pkgutil --forget com.xamarin.monotouch.pkg
sudo pkgutil --forget com.xamarin.xamarin-ios-build-host.pkg
sudo pkgutil --forget com.xamarin.xamarin.ios.pkg
```

## <a name="uninstall-xamarinmac"></a>Disinstallare Xamarin.Mac

È possibile rimuovere dal computer Xamarin.Mac usando i due comandi seguenti per eliminare rispettivamente il prodotto e la licenza dal Mac:

```bash
sudo rm -rf /Library/Frameworks/Xamarin.Mac.framework
rm -rf ~/Library/Xamarin.Mac
```

## <a name="uninstall-workbooks-and-inspector"></a>Disinstallare Workbooks e Inspector

A partire dalla versione 1.2.2, Xamarin Workbooks e Inspector possono essere disinstallati da un terminal eseguendo:

```bash
sudo /Library/Frameworks/Xamarin.Interactive.framework/Versions/Current/uninstall
```

Per le versioni precedenti, è necessario rimuovere manualmente gli artefatti seguenti:

* Eliminare l'app Workbooks all'indirizzo `"/Applications/Xamarin Workbooks.app"`
* Eliminare l'app Inspector `"Applications/Xamarin Inspector.app"`
* Eliminare i componenti aggiuntivi: `"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Interactive"` e `"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Inspector"`
* Eliminare Inspector e i file di supporto qui: `/Library/Frameworks/Xamarin.Interactive.framework` e `/Library/Frameworks/Xamarin.Inspector.framework`

## <a name="uninstall-the-xamarin-profiler"></a>Disinstallare Xamarin Profiler

```bash
sudo rm -rf "/Applications/Xamarin Profiler.app"
```

## <a name="uninstall-the-visual-studio-installer"></a>Disinstallare il Programma di installazione di Visual Studio

Usare i comandi seguenti per rimuovere tutte le tracce di Xamarin Universal Installer:

```bash
rm -rf ~/Library/Caches/XamarinInstaller/
rm -rf ~/Library/Caches/VisualStudioInstaller/
rm -rf ~/Library/Logs/XamarinInstaller/
rm -rf ~/Library/Logs/VisualStudioInstaller/
rm -rf ~/Library/Preferences/Xamarin/
rm -rf "~/Library/Preferences/Visual Studio/"
```

* * *

## <a name="uninstall-visual-studio-2019-for-mac-preview"></a>Disinstallare Visual Studio 2019 per Mac Preview

Visual Studio 2019 per Mac Preview viene avviato come anteprima distinta e consente di continuare a lavorare parallelamente con l'installazione di Visual Studio 2017 per Mac.

Ora che Visual Studio 2019 per Mac è stato rilasciato, è possibile rimuovere in modo sicuro l'applicazione Visual Studio 2019 per Mac Preview.

Per disinstallare il bundle dell'applicazione in anteprima, selezionare **Visual Studio (Preview)** nella cartella **Applicazioni** e fare clic su **Sposta nel cestino**, come illustrato nell'immagine seguente:

![selezione dell'opzione "Sposta nel cestino" in Finder](media/uninstall-remove-vspreview.png)

È possibile rimuovere il file con estensione plist dell'anteprima anche con il comando seguente:

```bash
rm -rf ~/Library/Preferences/com.microsoft.visual-studio-preview.plist
```

## <a name="see-also"></a>Vedi anche

- [Disinstallare Visual Studio (in Windows)](/visualstudio/install/uninstall-visual-studio)

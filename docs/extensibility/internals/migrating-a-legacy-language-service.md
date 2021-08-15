---
title: Migrazione di un servizio di linguaggio legacy | Microsoft Docs
description: Informazioni su come aggiornare un servizio di linguaggio alla versione più recente di Visual Studio aggiornando il progetto e aggiungendo un file source.extension.vsixmanifest.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, migrating
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 8530cb857310b20b8bcc83a654232df65d703fa23c61ee77913bf25f2f28740f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121321233"
---
# <a name="migrating-a-legacy-language-service"></a>Migrazione di un servizio di linguaggio legacy
È possibile eseguire la migrazione di un servizio di linguaggio legacy a una versione successiva di Visual Studio aggiornando il progetto e aggiungendo un file source.extension.vsixmanifest al progetto. Il servizio di linguaggio stesso continuerà a funzionare come in precedenza, perché l Visual Studio editor lo adatta.

 I servizi di linguaggio legacy vengono implementati come parte di un PACCHETTO VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio è usare le estensioni MEF. Per altre informazioni sul nuovo modo di implementare un servizio di linguaggio, vedere [Editor and Language Service Extensions](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> È consigliabile iniziare a usare la nuova API dell'editor appena possibile. Ciò consente di migliorare le prestazioni del servizio di linguaggio e di sfruttare le nuove funzionalità dell'editor.

## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>Migrazione di una soluzione Visual Studio 2008 Language Service a una versione successiva
 La procedura seguente illustra come adattare un Visual Studio 2008 denominato RegExLanguageService. È possibile trovare questo esempio in un'installazione di Visual Studio 2008 *SDK,* nella cartella percorso di installazione di Visual Studio SDK \VisualStudioIntegration\Samples\IDE\CSharp\Example.RegExLanguageService\.

> [!IMPORTANT]
> Se il servizio di linguaggio non definisce i colori, è necessario impostare in modo <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> `true` esplicito su nel pacchetto VSPackage:

```
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]
```

#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>Per eseguire la migrazione Visual Studio servizio di linguaggio di Visual Studio 2008 a una versione successiva

1. Installare le versioni più recenti di Visual Studio e Visual Studio SDK. Per altre informazioni su come installare l'SDK, vedere [Installing the Visual Studio SDK (Installazione di Visual Studio SDK).](../../extensibility/installing-the-visual-studio-sdk.md)

2. Modificare il file RegExLangServ.csproj (senza caricarlo in Visual Studio.

     Nel nodo `Import` che fa riferimento al file Microsoft.VsSDK.targets sostituire il valore con il testo seguente.

    ```
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets
    ```

3. Salvare il file e quindi chiuderlo.

4. Aprire la soluzione RegExLangServ.sln.

5. Viene **visualizzata la finestra Di aggiornamento unidiredato.** Fare clic su **OK**.

6. Aggiornare le proprietà del progetto. Aprire la finestra **Project proprietà** selezionando il nodo del progetto **nell'Esplora soluzioni**, facendo clic con il pulsante destro del mouse e scegliendo **Proprietà**.

    - Nella scheda **Applicazione** impostare **Framework di destinazione** su **4.6.1.**

    - Nella casella **Avvia** programma esterno **della** scheda Debug digitare **\<Visual Studio installation path>\Common7\IDE\devenv.exe.**.

         Nella casella **Argomenti della riga di** comando digitare /**rootsuffix Exp**.

7. Aggiornare i riferimenti seguenti:

    - Rimuovere il riferimento a Microsoft.VisualStudio.Shell.9.0.dll, quindi aggiungere riferimenti a Microsoft.VisualStudio.Shell.14.0.dll e Microsoft.VisualStudio.Shell.Immutable.11.0.dll.

    - Rimuovere il riferimento a Microsoft.VisualStudio.Package.LanguageService.9.0.dll, quindi aggiungere un riferimento a Microsoft.VisualStudio.Package.LanguageService.14.0.dll.

    - Aggiungere un riferimento a Microsoft.VisualStudio.Shell.Interop.10.0.dll.

8. Aprire il file VsPkg.cs e modificare il valore `DefaultRegistryRoot` dell'attributo in

    ```
    "Software\\Microsoft\\VisualStudio\\14.0Exp"
    ```

9. L'esempio originale non registra il servizio di linguaggio, quindi è necessario aggiungere l'attributo seguente a VsPkg.cs.

    ```
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]
    ```

10. È necessario aggiungere un file source.extension.vsixmanifest.

    - Copiare questo file da un'estensione esistente nella directory del progetto. Un modo per ottenere questo file è creare un progetto VSIX (in **File** fare clic su Nuovo **,** quindi fare clic su **Project**. In Visual Basic o C# fare clic su **Estendibilità**, quindi selezionare **VSIX Project**.

    - Aggiungere il file al progetto.

    - In Proprietà del file **impostare** Azione **di compilazione** su **Nessuno.**

    - Aprire il file con **l'Editor manifesto VSIX.**

    - Modificare i campi seguenti:

    - **ID:** RegExLangServ

    - **Nome prodotto:** RegExLangServ

    - **Descrizione:** servizio di linguaggio delle espressioni regolari.

    - In **Asset fare** clic su  **Nuovo,** selezionare Il tipo su  **Microsoft.VisualStudio.VsPackage,** impostare Origine su **Un** progetto nella soluzione corrente e quindi impostare il **Project** su **RegExLangServ.**

    - Salvare e chiudere il file.

11. Compilare la soluzione. I file compilati vengono distribuiti in **%USERPROFILE%\AppData\Local\Microsoft\VisualStudio\14.0Exp\Extensions\MSIT\ \\ RegExLangServ**.

12. Avviare il debug. Viene aperta una seconda istanza Visual Studio.

## <a name="see-also"></a>Vedi anche
- [Estendibilità dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-extensibility.md)

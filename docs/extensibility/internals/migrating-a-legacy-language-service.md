---
title: Migrazione di un servizio di linguaggio legacy | Microsoft Docs
description: Per informazioni su come aggiornare un servizio di linguaggio alla versione più recente di Visual Studio, aggiornare il progetto e aggiungere un file source. Extension. vsixmanifest.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, migrating
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ced200ff24b17f312e63642c8083f038a6fc6a4d
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877832"
---
# <a name="migrating-a-legacy-language-service"></a>Migrazione di un servizio di linguaggio legacy
Per eseguire la migrazione di un servizio di linguaggio legacy a una versione successiva di Visual Studio, è possibile aggiornare il progetto e aggiungere un file source. Extension. vsixmanifest al progetto. Il servizio di linguaggio stesso continuerà a funzionare come prima, perché l'editor di Visual Studio lo adatta.

 I servizi di linguaggio legacy sono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per ulteriori informazioni sul nuovo modo per implementare un servizio di linguaggio, vedere [Editor e le estensioni del servizio di linguaggio](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Si consiglia di iniziare a usare la nuova API editor appena possibile. Ciò consente di migliorare le prestazioni del servizio di linguaggio e di sfruttare i vantaggi delle nuove funzionalità dell'editor.

## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>Migrazione di una soluzione di servizio di linguaggio Visual Studio 2008 a una versione successiva
 I passaggi seguenti illustrano come adattare un esempio di Visual Studio 2008 denominato RegExLanguageService. È possibile trovare questo esempio in un'installazione di Visual Studio 2008 SDK, nella cartella \VisualStudioIntegration\Samples\IDE\CSharp\Example.RegExLanguageService\ del *percorso di installazione di Visual Studio SDK*.

> [!IMPORTANT]
> Se il servizio di linguaggio non definisce i colori, è necessario impostare in modo esplicito <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> `true` su nel pacchetto VSPackage:

```
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]
```

#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>Per eseguire la migrazione di un servizio di linguaggio Visual Studio 2008 a una versione successiva

1. Installare le versioni più recenti di Visual Studio e Visual Studio SDK. Per ulteriori informazioni sulle modalità di installazione dell'SDK, vedere [installazione di Visual Studio SDK](../../extensibility/installing-the-visual-studio-sdk.md).

2. Modificare il file RegExLangServ. csproj senza caricarlo in Visual Studio.

     Nel `Import` nodo che fa riferimento al file Microsoft. VsSDK. targets sostituire il valore con il testo seguente.

    ```
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets
    ```

3. Salvare il file e quindi chiuderlo.

4. Aprire la soluzione RegExLangServ. sln.

5. Viene visualizzata la finestra di **aggiornamento unidirezionale** . Fare clic su **OK**.

6. Aggiornare le proprietà del progetto. Aprire la finestra delle **proprietà del progetto** selezionando il nodo del progetto nella **Esplora soluzioni**, facendo clic con il pulsante destro del mouse e scegliendo **proprietà**.

    - Nella scheda **applicazione** impostare Framework di **destinazione** su **4.6.1**.

    - Nella scheda **debug** , nella casella **Avvia programma esterno** , digitare **\<Visual Studio installation path>\Common7\IDE\devenv.exe.**.

         Nella casella **argomenti della riga di comando** Digitare/**rootsuffix exp**.

7. Aggiornare i riferimenti seguenti:

    - Rimuovere il riferimento a Microsoft.VisualStudio.Shell.9.0.dll, quindi aggiungere i riferimenti a Microsoft.VisualStudio.Shell.14.0.dll e Microsoft.VisualStudio.Shell.Immutable.11.0.dll.

    - Rimuovere il riferimento a Microsoft.VisualStudio.Package.LanguageService.9.0.dll, quindi aggiungere un riferimento a Microsoft.VisualStudio.Package.LanguageService.14.0.dll.

    - Aggiungere un riferimento a Microsoft.VisualStudio.Shell.Interop.10.0.dll.

8. Aprire il file VsPkg.cs e modificare il valore dell' `DefaultRegistryRoot` attributo in

    ```
    "Software\\Microsoft\\VisualStudio\\14.0Exp"
    ```

9. L'esempio originale non registra il servizio di linguaggio, quindi è necessario aggiungere l'attributo seguente a VsPkg.cs.

    ```
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]
    ```

10. È necessario aggiungere un file source. Extension. vsixmanifest.

    - Copiare questo file da un'estensione esistente alla directory del progetto. Un modo per ottenere questo file consiste nel creare un progetto VSIX (in **file**, fare clic su **nuovo**, quindi su **progetto**. In Visual Basic o C# fare clic su **estendibilità**, quindi selezionare **progetto VSIX**.

    - Aggiungere il file al progetto.

    - Nelle **Proprietà** del file impostare azione di **compilazione** su **nessuno**.

    - Aprire il file con l' **Editor del manifesto VSIX**.

    - Modificare i campi seguenti:

    - **ID**: RegExLangServ

    - **Nome prodotto**: RegExLangServ

    - **Descrizione**: servizio di linguaggio di espressioni regolari.

    - In **Asset** fare clic **su nuovo**, selezionare il **tipo** in **Microsoft. VisualStudio. VSPackage**, impostare l' **origine** su **un progetto nella soluzione corrente**, quindi impostare il **progetto** su **RegExLangServ**.

    - Salvare e chiudere il file.

11. Compilare la soluzione. I file compilati vengono distribuiti in **%USERPROFILE%\AppData\Local\Microsoft\VisualStudio\14.0Exp\Extensions\MSIT\ RegExLangServ \\**.

12. Avviare il debug. È stata aperta una seconda istanza di Visual Studio.

## <a name="see-also"></a>Vedi anche
- [Estendibilità dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-extensibility.md)

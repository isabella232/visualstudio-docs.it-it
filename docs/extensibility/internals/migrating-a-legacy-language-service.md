---
title: Migrazione di un servizio di linguaggio Legacy Documenti Microsoft
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
ms.openlocfilehash: 9e2eff3f3a27b7d8a276c8ed776c1e11d5ce332e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707105"
---
# <a name="migrating-a-legacy-language-service"></a>Migrazione di un servizio di linguaggio legacy
È possibile eseguire la migrazione di un servizio di linguaggio legacy a una versione successiva di Visual Studio aggiornando il progetto e aggiungendo un file source.extension.vsixmanifest al progetto. Il servizio di linguaggio stesso continuerà a funzionare come prima, perché l'editor di Visual Studio lo adatta.

 Servizi di linguaggio legacy vengono implementati come parte di un VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'utilizzare le estensioni MEF. Per ulteriori informazioni sul nuovo modo di implementare un servizio di linguaggio, vedere [Editor e estensioni del servizio](../../extensibility/editor-and-language-service-extensions.md)di linguaggio .

> [!NOTE]
> Si consiglia di iniziare a utilizzare la nuova API dell'editor il prima possibile. Ciò migliorerà le prestazioni del servizio di linguaggio e consentirà di sfruttare le nuove funzionalità dell'editor.

## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>Migrazione di una soluzione del servizio di linguaggio di Visual Studio 2008 a una versione successivaMigrating a Visual Studio 2008 Language Service Solution to a Later Version
 I passaggi seguenti illustrano come adattare un esempio di Visual Studio 2008 denominato RegExLanguageService.The following steps show how to adapt a Visual Studio 2008 sample named RegExLanguageService. È possibile trovare questo esempio in un'installazione di Visual Studio 2008 SDK, nella cartella di installazione di *Visual Studio SDK.*

> [!IMPORTANT]
> Se il servizio di linguaggio non <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> definisce i colori, è necessario impostare in modo esplicito su nel pacchetto VSPackage:If your language service does not define colors, you must explicitly set to `true` on the VSPackage:

```
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]
```

#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>Per eseguire la migrazione di un servizio di linguaggio di Visual Studio 2008 a una versione successivaTo migrate a Visual Studio 2008 language service to a later version

1. Installare le versioni più recenti di Visual Studio e Visual Studio SDK. Per ulteriori informazioni sulle modalità di installazione dell'SDK, vedere [Installazione di Visual Studio SDK](../../extensibility/installing-the-visual-studio-sdk.md).

2. Modificare il file RegExLangServ.csproj (senza caricarlo in Visual Studio.

     Nel `Import` nodo che fa riferimento al file Microsoft.VsSDK.targets sostituire il valore con il testo seguente.

    ```
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets
    ```

3. Salvare il file e quindi chiuderlo.

4. Aprire la soluzione RegExLangServ.sln.

5. Viene visualizzata la finestra **di aggiornamento unidirezionale.** Fare clic su **OK**.

6. Aggiornare le proprietà del progetto. Aprire la finestra **Proprietà progetto** selezionando il nodo del progetto in **Esplora soluzioni**, facendo clic con il pulsante destro del mouse e scegliendo **Proprietà**.

    - Nella scheda **Applicazione** modificare Framework di **destinazione** in **4.6.1**.

    - Nella casella **Avvia programma esterno** della scheda **Debug** digitare ** \<percorso**di installazione di Visual Studio>.

         Nella casella **Argomenti della riga** di comando digitare /**rootsuffix Exp**.

7. Aggiornare i seguenti riferimenti:

    - Rimuovere il riferimento a Microsoft.VisualStudio.Shell.9.0.dll, quindi aggiungere riferimenti a Microsoft.VisualStudio.Shell.14.0.dll e Microsoft.VisualStudio.Shell.Immutable.11.0.dll.

    - Rimuovere il riferimento a Microsoft.VisualStudio.Package.LanguageService.9.0.dll, quindi aggiungere un riferimento a Microsoft.VisualStudio.Package.LanguageService.14.0.dll.

    - Aggiungere un riferimento a Microsoft.VisualStudio.Shell.Interop.10.0.dll.Add a reference to Microsoft.VisualStudio.Shell.Interop.10.0.dll.

8. Aprire il file VsPkg.cs e `DefaultRegistryRoot` modificare il valore dell'attributo in

    ```
    "Software\\Microsoft\\VisualStudio\\14.0Exp"
    ```

9. L'esempio originale non registra il servizio di linguaggio, pertanto è necessario aggiungere l'attributo seguente a VsPkg.cs.

    ```
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]
    ```

10. È necessario aggiungere un file source.extension.vsixmanifest.

    - Copiare questo file da un'estensione esistente nella directory del progetto. Un modo per ottenere questo file consiste nel creare un progetto VSIX (in **File**, fare clic su **Nuovo**, quindi su **Progetto**. In Visual Basic o c'è clic su **Estensibilità**, quindi selezionare **Progetto VSIX**.)

    - Aggiungere il file al progetto.

    - Nelle **proprietà**del file impostare Azione di **compilazione** su **Nessuno**.

    - Aprire il file con **l'Editor del manifesto VSIX**.

    - Modificare i seguenti campi:

    - **ID**: RegExLangServ

    - **Nome prodotto**: RegExLangServ

    - **Descrizione**: Un servizio di linguaggio delle espressioni regolari.

    - In **Risorse**fare clic su **Nuovo**, selezionare **Tipo su** **Microsoft.VisualStudio.VsPackage**, impostare **Origine** su Progetto nella **soluzione corrente**, quindi impostare Il progetto **su** **RegExLangServ**.

    - Salvare e chiudere il file.

11. Compilare la soluzione. I file compilati vengono distribuiti in **%USERPROFILE% AppData Locale Microsoft MicrosoftVisualStudio 14.0Exp .\\**

12. Avviare il debug. Una seconda istanza di Visual Studio aperta.

## <a name="see-also"></a>Vedere anche
- [Estendibilità dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-extensibility.md)

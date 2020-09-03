---
title: Distribuzione di un processore di direttiva personalizzato | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
ms.assetid: 80c28722-a630-47b5-923b-024dc3f2c940
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6cce0a918b1b3e029846176832ab2feb74e3e9e4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669843"
---
# <a name="deploying-a-custom-directive-processor"></a>Distribuzione di un processore di direttiva personalizzato
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per utilizzare un processore di direttiva personalizzato in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in un computer qualsiasi, è necessario registrarlo da uno dei metodi descritti in questo argomento.

 I metodi alternativi sono i seguenti:

- [Estensione di Visual Studio (VSIX)](https://msdn.microsoft.com/64ff1452-f7d5-42d9-98b8-76f769f76832). Fornisce un modo per installare e disinstallare il processore di direttiva sia in un proprio computer che in altri computer. In genere, è possibile comprimere altre funzionalità nello stesso VSIX.

- [Pacchetto VSPackage](../extensibility/internals/vspackages.md). Se si definisce un package VS che contiene altre funzionalità oltre al processore di direttiva, esiste un metodo comodo per registrare il processore di direttiva.

- Impostare una chiave del Registro di sistema. In questo metodo, si aggiunge una voce del Registro di sistema per il processore di direttiva.

  È necessario utilizzare uno di questi metodi solo se si desidera trasformare il modello di testo in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] o [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Se si utilizza un host personalizzato nella propria applicazione, l'host personalizzato è responsabile dell'individuazione dei processori di direttive per ciascuna direttiva.

## <a name="deploying-a-directive-processor-in-a-vsix"></a>Distribuzione di un processore di direttiva in un pacchetto VSIX
 È possibile aggiungere un processore di direttiva personalizzato a un' [estensione di Visual Studio (VSIX)](https://msdn.microsoft.com/64ff1452-f7d5-42d9-98b8-76f769f76832).

 È necessario assicurarsi che i due elementi seguenti siano contenuti nel file .vsix:

- L'assembly (.dll) che contiene la classe del processore di direttiva personalizzata.

- Un file .pkgdef che registra il processore di direttiva. Il nome radice del file deve essere uguale all'assembly. Ad esempio, i file potrebbero essere denominati CDP.dll e CDP.pkgdef.

  Per esaminare o modificare il contenuto di un file .vsix, cambiare l'estensione del file in .zip, quindi aprirlo. Dopo avere modificato il contenuto, reimpostare l'estensione del file su .vsix.

  Esistono diversi modi di creare un file .vsix. Nella procedura seguente ne viene descritto uno.

#### <a name="to-develop-a-custom-directive-processor-in-a-vsix-project"></a>Per sviluppare un processore di direttiva personalizzato in un progetto VSIX

1. Creare un progetto VSIX in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

    - Nella finestra di dialogo **nuovo progetto** espandere **Visual Basic** o **Visual C#**, quindi espandere **estensibilità**. Fare clic su **progetto VSIX**.

2. In **source. Extension. vsixmanifest**impostare il tipo di contenuto e le edizioni supportate.

    1. Nell'editor del manifesto VSIX, nella scheda **Asset** , scegliere **nuovo** e impostare le proprietà del nuovo elemento:

         **Tipo**  =  di contenuto **Pacchetto VSPackage**

         **Progetto di origine** = \<*the current project*>

    2. Fare clic su **edizioni selezionate** e controllare i tipi di installazione in cui si desidera che il processore di direttiva sia utilizzabile.

3. Aggiungere un file .pkgdef e impostarne le proprietà da includere in VSIX.

    1. Creare un file di testo e denominarlo \<*assemblyName*> . pkgdef.

         \<*assemblyName*> corrisponde in genere al nome del progetto.

    2. Selezionarlo in Esplora soluzioni e impostarne le proprietà come segue:

         **Azione**  =  di compilazione **Contenuto** di

         **Copia nella directory**  =  di output **Copia sempre**

         **Includi in VSIX**  =  Valore **true**

    3. Impostare il nome del pacchetto VSIX e assicurarsi che l'ID sia univoco.

4. Aggiungere il seguente testo al file .pkgdef.

    ```
    [$RootKey$\TextTemplating]
    [$RootKey$\TextTemplating\DirectiveProcessors]
    [$RootKey$\TextTemplating\DirectiveProcessors\ CustomDirectiveProcessorName]
    @="Custom Directive Processor description"
    "Class"="NamespaceName.ClassName"
    "CodeBase"="$PackageFolder$\AssemblyName.dll"
    ```

     Sostituire i nomi seguenti con i propri nomi: `CustomDirectiveProcessorName`, `NamespaceName`, `ClassName`, `AssemblyName`.

5. Aggiungere i riferimenti seguenti al progetto:

    - **Microsoft. VisualStudio. TextTemplating. \* . 0**

    - **Microsoft. VisualStudio. TextTemplating. Interfaces. \* . 0**

    - **Microsoft. VisualStudio. TextTemplating. VSHost. \* . 0**

6. Aggiungere la classe del processore di direttiva personalizzato al progetto.

     Si tratta di una classe pubblica che deve implementare <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> o <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.

#### <a name="to-install-the-custom-directive-processor"></a>Per installare il processore di direttiva personalizzato

1. In Esplora risorse, aprire la directory di compilazione (in genere è bin\Debug o bin\Release).

2. Se si desidera installare il processore di direttiva in un altro computer, copiare il file .vsix nell'altro computer.

3. Fare doppio clic sul file .vsix. Verrà visualizzato [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Extension Installer.

4. Riavviare [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Si sarà ora in grado di eseguire modelli di testo che contengono direttive che si riferiscono al processore di direttiva personalizzato. Ogni direttiva è nel seguente formato:

     `<#@ CustomDirective Processor="CustomDirectiveProcessorName" parameter1="value1" … #>`

#### <a name="to-uninstall-or-temporarily-disable-the-custom-directive-processor"></a>Per disinstallare o disabilitare temporaneamente il processore di direttiva personalizzato

1. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Scegliere **Gestione estensioni**dal menu **strumenti** .

2. Selezionare il progetto VSIX che contiene il processore di direttiva, quindi fare clic su **Disinstalla** o **Disabilita**.

### <a name="troubleshooting-a-directive-processor-in-a-vsix"></a>Risoluzione dei problemi relativi a un processore di direttiva in un pacchetto VSIX
 Se il processore di direttiva non funziona, è possibile seguire i suggerimenti indicati di seguito:

- Il nome del processore che si specifica nella direttiva personalizzata deve corrispondere al `CustomDirectiveProcessorName` specificato nel file .pkgdef.

- Il metodo `IsDirectiveSupported` deve restituire `true` quando viene passato il nome di `CustomDirective`.

- Se l'estensione non è visibile in Gestione estensioni, ma il sistema non consentirà di installarlo, eliminare l'estensione da **%LocalAppData%\Microsoft\VisualStudio \\ \* . 0 \ Extensions \\ **.

- Aprire il file .vsix ed esaminarne il contenuto. Per aprirlo, impostare l'estensione del file su .zip. Verificare che contenga i file .dll, .pkgdef ed extension.vsixmanifest. Il file extension.vsixmanifest deve contenere l'elenco adatto nel nodo SupportedProducts e deve contenere anche un nodo Package VS sotto il nodo Contenuto:

     `<Content>`

     `<VsPackage>CustomDirectiveProcessor.dll</VsPackage>`

     `</Content>`

## <a name="deploying-a-directive-processor-in-a-vspackage"></a>Distribuzione di un processore di direttiva in un package VS
 Se il processore di direttiva fa parte di un package VS che sarà installato nella GAC, è possibile fare in modo che sia il sistema a generare il file .pkgdef.

 Posizionare l'attributo seguente sulla classe del package:

```
[ProvideDirectiveProcessor(typeof(DirectiveProcessorClass), "DirectiveProcessorName", "Directive processor description.")]
```

> [!NOTE]
> Questo attributo viene posizionato sulla classe del package, non sulla classe del processore di direttiva.

 Il file .pkgdef sarà generato quando si compila il progetto. Quando si installa il package VS, nel file .pkgdef verrà registrato il processore di direttiva.

 Verificare che il file .pkgdef venga visualizzato nella cartella di compilazione, che in genere è bin\Debug o bin\Release. Se non è visualizzato, aprire il file .csproj in un editor di testo e rimuovere il nodo seguente: `<GeneratePkgDefFile>false</GeneratePkgDefFile>`.

 Per altre informazioni, vedere [VSPackages](../extensibility/internals/vspackages.md).

## <a name="setting-a-registry-key"></a>Impostazione di una chiave di Registro di sistema
 Questo metodo per installare un processore di direttiva personalizzato è il meno preferito. Non fornisce un modo comodo per abilitare e disabilitare il processore di direttiva e non fornisce un metodo per distribuire il processore di direttiva ad altri utenti.

> [!CAUTION]
> Se il Registro di sistema viene modificato in modo non appropriato, il sistema potrebbe venire gravemente danneggiato. Prima di apportare modifiche al Registro di sistema, eseguire il backup dei dati importanti sul computer.

#### <a name="to-register-a-directive-processor-by-setting-a-registry-key"></a>Per registrare un processore di direttiva impostando una chiave del Registro di sistema

1. Eseguire `regedit`.

2. In regedit passare a

    **HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ \* . 0 \ TextTemplating\DirectiveProcessors**

    Se si desidera installare il processore di direttiva nella versione sperimentale di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], inserire "Exp" dopo "11.0".

3. Aggiungere una chiave del Registro di sistema che abbia lo stesso nome della classe del processore di direttiva.

   - Nell'albero del registro di sistema fare clic con il pulsante destro del mouse sul nodo **DirectiveProcessors** , scegliere **nuovo**, quindi fare clic su **chiave**.

4. Nel nuovo nodo, aggiungere valori stringa per Class e CodeBase o Assembly, sulla base delle tabelle seguenti.

   1. Fare clic con il pulsante destro del mouse sul nodo creato, scegliere **nuovo**, quindi fare clic su **valore stringa**.

   2. Modificare il nome del valore.

   3. Fare doppio clic sul nome e modificare i dati.

   Se il processore di direttiva personalizzato non è presente nella GAC, le sottochiavi del Registro di sistema appariranno come indicato nella tabella seguente:

|Nome|Type|Dati|
|----------|----------|----------|
|Valore predefinito.|REG_SZ|(valore non impostato)|
|Classe|REG_SZ|**\<Namespace Name>.\<Class Name>**|
|CodeBase|REG_SZ|**\<Your Path>\\<il nome dell'assembly\>**|

 Se l'assembly è presente nella GAC, le sottochiavi del Registro di sistema appariranno come indicato nella tabella seguente:

|Nome|Type|Dati|
|----------|----------|----------|
|Valore predefinito.|REG_SZ|(valore non impostato)|
|Classe|REG_SZ|\<**Your Fully Qualified Class Name**>|
|Assembly|REG_SZ|\<**Your Assembly Name in the GAC**>|

## <a name="see-also"></a>Vedere anche
 [Creazione di processori di direttiva di modelli di testo T4 personalizzati](../modeling/creating-custom-t4-text-template-directive-processors.md)

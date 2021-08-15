---
title: Distribuzione di un processore di direttiva personalizzato
description: Informazioni sui metodi disponibili per la distribuzione di un processore di direttiva personalizzato in Visual Studio o in qualsiasi computer.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- text templates, custom directive processors
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 4dcc9f12a65ad163acd07724da534039c772b385446f00b30dab627d441a42fc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121316864"
---
# <a name="deploying-a-custom-directive-processor"></a>Distribuzione di un processore di direttiva personalizzato

Per usare un processore di direttiva personalizzato Visual Studio in qualsiasi computer, è necessario registrarlo con uno dei metodi descritti in questo argomento.

I metodi alternativi sono i seguenti:

- [Visual Studio estensioni .](../extensibility/shipping-visual-studio-extensions.md) Fornisce un modo per installare e disinstallare il processore di direttiva sia in un proprio computer che in altri computer. In genere, è possibile comprimere altre funzionalità nello stesso VSIX.

- [VSPackage](../extensibility/internals/vspackages.md). Se si definisce un package VS che contiene altre funzionalità oltre al processore di direttiva, esiste un metodo comodo per registrare il processore di direttiva.

- Impostare una chiave del Registro di sistema. In questo metodo, si aggiunge una voce del Registro di sistema per il processore di direttiva.

È necessario usare uno di questi metodi solo se si vuole trasformare il modello di testo in Visual Studio o MSBuild. Se si utilizza un host personalizzato nella propria applicazione, l'host personalizzato è responsabile dell'individuazione dei processori di direttive per ciascuna direttiva.

## <a name="deploying-a-directive-processor-in-a-vsix"></a>Distribuzione di un processore di direttiva in un pacchetto VSIX

È possibile aggiungere un processore di direttiva personalizzato a [Visual Studio Extension (VSIX).](../extensibility/starting-to-develop-visual-studio-extensions.md)

 È necessario assicurarsi che i due elementi seguenti siano contenuti nel file .vsix:

- L'assembly (.dll) che contiene la classe del processore di direttiva personalizzata.

- Un file .pkgdef che registra il processore di direttiva. Il nome radice del file deve essere uguale all'assembly. Ad esempio, i file potrebbero essere denominati CDP.dll e CDP.pkgdef.

Per esaminare o modificare il contenuto di un file .vsix, cambiare l'estensione del file in .zip, quindi aprirlo. Dopo avere modificato il contenuto, reimpostare l'estensione del file su .vsix.

Esistono diversi modi di creare un file .vsix. Nella procedura seguente ne viene descritto uno.

#### <a name="to-develop-a-custom-directive-processor-in-a-vsix-project"></a>Per sviluppare un processore di direttiva personalizzato in un progetto VSIX

1. Creare un nuovo **progetto Project VSIX.**

2. In **source.extension.vsixmanifest** impostare il tipo di contenuto e le edizioni supportate.

    1. Nella scheda Asset dell'editor  manifesto VSIX scegliere **Nuovo** e impostare le proprietà del nuovo elemento:

         **Tipo di contenuto**  =  **VSPackage**

         **Origine Project** = \<*the current project*>

    2. Fare **clic su Edizioni selezionate** e controllare i tipi di installazione in cui si vuole che il processore di direttiva sia utilizzabile.

3. Aggiungere un file .pkgdef e impostarne le proprietà da includere in VSIX.

    1. Creare un file di testo e assegnare al file \<*assemblyName*> il nome .pkgdef.

         \<*assemblyName*> è in genere uguale al nome del progetto.

    2. Selezionarlo in Esplora soluzioni e impostarne le proprietà come segue:

         **Azione di compilazione**  =  **Contenuto**

         **Copia nella directory di output**  =  **Copia sempre**

         **Includere in VSIX**  =  **True**

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

    - **Microsoft.VisualStudio.TextTemplating. \* . 0**

    - **Microsoft.VisualStudio.TextTemplating.Interfaces. \* 0**

    - **Microsoft.VisualStudio.TextTemplating.VSHost. \* . 0**

6. Aggiungere la classe del processore di direttiva personalizzato al progetto.

     Si tratta di una classe pubblica che deve implementare <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> o <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.

#### <a name="to-install-the-custom-directive-processor"></a>Per installare il processore di direttiva personalizzato

1. In Windows Explorer aprire la directory di compilazione (in genere bin\Debug o bin\Release).

2. Se si desidera installare il processore di direttiva in un altro computer, copiare il file .vsix nell'altro computer.

3. Fare doppio clic sul file .vsix. Viene visualizzato Visual Studio programma di installazione dell'estensione.

4. Riavviare Visual Studio. Si sarà ora in grado di eseguire modelli di testo che contengono direttive che si riferiscono al processore di direttiva personalizzato. Ogni direttiva è nel seguente formato:

     `<#@ CustomDirective Processor="CustomDirectiveProcessorName" parameter1="value1" ... #>`

#### <a name="to-uninstall-or-temporarily-disable-the-custom-directive-processor"></a>Per disinstallare o disabilitare temporaneamente il processore di direttiva personalizzato

1. Nel menu Visual Studio **strumenti fare** clic su **Gestione estensioni**.

2. Selezionare il file VSIX che contiene il processore di direttiva e quindi fare clic **su Disinstalla** o **Disabilita**.

### <a name="troubleshooting-a-directive-processor-in-a-vsix"></a>Risoluzione dei problemi relativi a un processore di direttiva in un pacchetto VSIX
 Se il processore di direttiva non funziona, è possibile seguire i suggerimenti indicati di seguito:

- Il nome del processore che si specifica nella direttiva personalizzata deve corrispondere al `CustomDirectiveProcessorName` specificato nel file .pkgdef.

- Il metodo `IsDirectiveSupported` deve restituire `true` quando viene passato il nome di `CustomDirective`.

- Se non è possibile visualizzare l'estensione in Gestione estensioni, ma il sistema non consente di installarla, eliminare l'estensione da **%localappdata%\Microsoft\VisualStudio \\ \* .0\Extensions \\**.

- Aprire il file .vsix ed esaminarne il contenuto. Per aprirlo, impostare l'estensione del file su .zip. Verificare che contenga i file .dll, .pkgdef ed extension.vsixmanifest. Il file extension.vsixmanifest deve contenere l'elenco adatto nel nodo SupportedProducts e deve contenere anche un nodo Package VS sotto il nodo Contenuto:

     `<Content>`

     `<VsPackage>CustomDirectiveProcessor.dll</VsPackage>`

     `</Content>`

## <a name="deploying-a-directive-processor-in-a-vspackage"></a>Distribuzione di un processore di direttiva in un package VS
 Se il processore di direttiva fa parte di un package VS che sarà installato nella GAC, è possibile fare in modo che sia il sistema a generare il file .pkgdef.

 Posizionare l'attributo seguente sulla classe del package:

```csharp
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

    **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ \* .0\TextTemplating\DirectiveProcessors**

    Se si vuole installare il processore di direttiva nella versione sperimentale di Visual Studio, inserire "Exp" dopo "11.0".

3. Aggiungere una chiave del Registro di sistema che abbia lo stesso nome della classe del processore di direttiva.

   - Nell'albero del Registro di sistema fare clic con il pulsante destro del mouse **sul nodo DirectiveProcessors,** scegliere **Nuovo** e quindi fare clic su **Chiave**.

4. Nel nuovo nodo, aggiungere valori stringa per Class e CodeBase o Assembly, sulla base delle tabelle seguenti.

   1. Fare clic con il pulsante destro del mouse sul nodo creato, scegliere **Nuovo** e quindi fare clic su **Valore stringa**.

   2. Modificare il nome del valore.

   3. Fare doppio clic sul nome e modificare i dati.

   Se il processore di direttiva personalizzato non è presente nella GAC, le sottochiavi del Registro di sistema appariranno come indicato nella tabella seguente:

|Nome|Tipo|Dati|
|-|-|-|
|Valore predefinito.|REG_SZ|(valore non impostato)|
|Classe|REG_SZ|**\<Namespace Name>.\<Class Name>**|
|CodeBase|REG_SZ|**\<Your Path>\\<nome dell'assembly\>**|

 Se l'assembly è presente nella GAC, le sottochiavi del Registro di sistema appariranno come indicato nella tabella seguente:

|Nome|Tipo|Dati|
|-|-|-|
|Valore predefinito.|REG_SZ|(valore non impostato)|
|Classe|REG_SZ|\<**Your Fully Qualified Class Name**>|
|Assembly|REG_SZ|\<**Your Assembly Name in the GAC**>|

## <a name="see-also"></a>Vedi anche

- [Creazione di processori di direttiva di modelli di testo T4 personalizzati](../modeling/creating-custom-t4-text-template-directive-processors.md)

---
title: L'aggiornamento di progetto personalizzato e i modelli di elemento per Visual Studio "15" | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 02c7b14051a41616ed1b98812d1f1b7762f7165e
ms.sourcegitcommit: aea5cdb76fbc7eb31d1e5cc3c8d6adb0c743220f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2018
ms.locfileid: "47590901"
---
# <a name="upgrading-custom-project-and-item-templates-for-visual-studio-15"></a>L'aggiornamento di progetto personalizzato e i modelli di elemento per Visual Studio "15"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [l'aggiornamento Custom Project and Item Templates for Visual Studio ](https://docs.microsoft.com/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017).  
  
A partire da Visual Studio "15" Preview 4, Visual Studio sta cambiando il modo consente di individuare i modelli di progetti ed elementi installati da un file con estensione msi o un'estensione VSIX. Se si possiedono le estensioni che usano i modelli di elemento o progetto personalizzato, è necessario aggiornare le estensioni. Questo argomento illustra le operazioni da eseguire.  
  
 Questa modifica riguarda solo Visual Studio "15". Non influisce sulle versioni precedenti di Visual Studio.  
  
 Se si desidera creare un modello di progetto o un elemento come parte di un'estensione VSIX, vedere [creazione Custom Project and Item Templates](../extensibility/creating-custom-project-and-item-templates.md).  
  
## <a name="template-scanning"></a>Modello di analisi  
 In precedenza **devenv /setup** oppure **devenv /installvstemplates** analizzati nel disco locale per trovare i modelli di progetto ed elemento. A partire dalla versione Preview 4, l'analisi verrà eseguita solo per il percorso a livello di utente (**%USERPROFILE%\Documents\\< versione di Visual Studio\>\My Exported Templates\\**) che viene utilizzato per i modelli generati dal **File / esportare modelli** comando.  
  
 Per altre posizioni (non-utente), è necessario includere un file manifest(.vstman) che specifica il percorso e altre caratteristiche del modello. Viene generato il file con estensione vstman insieme al file con estensione vstemplate utilizzato per i modelli. Se si installa l'estensione usando un'estensione VSIX, è possibile farlo tramite la ricompilazione l'estensione di Visual Studio "15" Preview 2. Ma se si usa un file con estensione msi, è necessario apportare le modifiche manualmente. Per un elenco di ciò che occorre fare per apportare queste modifiche, vedere **gli aggiornamenti per le estensioni installate con un. Identità del servizio gestito** più avanti in questo argomento.  
  
## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Come aggiornare un'estensione VSIX con i modelli di elemento o progetto  
 In questa procedura viene descritto come ottenere l'aggiornamento di Visual Studio "15" Preview 2 l'estensione VSIX esistente.  
  
1.  Aprire la soluzione in Visual Studio "15" Preview 2. Verrà richiesto di aggiornare il codice. Fare clic su **OK**.  
  
2.  Al termine dell'aggiornamento, si potrebbe essere necessario modificare la versione della destinazione di installazione. Nel progetto VSIX, aprire il file vsixmanifest e selezionare il **destinazioni di installazione** scheda. Se il **intervallo di versioni** campo **[14.0]**, fare clic su **Edit** e modificare in modo da includere Visual Studio "15". Ad esempio, è possibile impostare **[14.0,15.0]** per installare l'estensione di Visual Studio 2015 o Visual Studio "15", o in **[15.0]** per installarlo solo Visual Studio "15".  
  
3.  Ricompilare il codice.  
  
4.  Chiudere Visual Studio.  
  
5.  Installare l'estensione VSIX.  
  
6.  È possibile testare l'aggiornamento eseguendo queste operazioni:  
  
    1.  L'analisi dei modifica il file viene attivato mediante la chiave del Registro di sistema seguente:  
  
         **REG aggiungere hklm\software\microsoft\visualstudio\15.0\VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**  
  
    2.  Dopo aver aggiunto la chiave, eseguire **devenv /installvstemplates**.  
  
    3.  Riaprire Visual Studio. È necessario trovare il modello nel percorso previsto.  
  
    > [!NOTE]
    >  I modelli di progetto Extensibility di Visual Studio non sono disponibili quando la chiave del Registro di sistema è presente. È necessario eliminare la chiave del Registro di sistema (e rieseguire **devenv /installvstemplates**) di utilizzarli.  
  
## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Altri suggerimenti per la distribuzione di Project and Item Templates  
  
-   Evitare di usare i file di modello compresso. Compressi in file devono essere compressi per recuperare le risorse e il contenuto modello pertanto saranno costlier da usare. In alternativa, è consigliabile distribuire i modelli di progetti ed elementi come file singoli nella propria directory per velocizzare l'inizializzazione di modello. Per le estensioni VSIX, le attività di compilazione SDK decomprimerà automaticamente qualsiasi modello compresso durante la creazione del file VSIX.  
  
-   Evitare di usare le voci di ID pacchetto/risorsa per il nome del modello, descrizione, icona o anteprima per evitare di caricamenti di assembly di risorse non necessarie durante l'individuazione dei modelli. In alternativa, è possibile utilizzare manifesti localizzati per creare una voce di modello per ogni impostazione locale, che Usa nomi localizzati o proprietà.  
  
-   Se si includono i modelli come elementi del file, la generazione del manifesto potrebbe non fornire i risultati previsti. In tal caso, è necessario aggiungere un manifesto generato manualmente al progetto VSIX.  
  
## <a name="file-changes-in-project-and-item-templates"></a>Modifiche ai file nel progetto e modelli di elemento  
 Verranno illustrati i punti della differenza tra la versione di Visual Studio 2015 e la versione di Visual Studio "15" dei file di modello, in modo che sia possibile creare i nuovi file in modo corretto.  
  
 Ecco il file con estensione vstemplate di progetto predefinito creato da Visual Studio 2015:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">  
  <TemplateData>  
    <Name>ProjectTemplate1</Name>  
    <Description>ProjectTemplate1</Description>  
    <Icon>ProjectTemplate1.ico</Icon>  
    <ProjectType>CSharp</ProjectType>  
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
    <SortOrder>1000</SortOrder>  
    <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>  
    <CreateNewFolder>true</CreateNewFolder>  
    <DefaultName>ProjectTemplate1</DefaultName>  
    <ProvideDefaultName>true</ProvideDefaultName>  
  </TemplateData>  
  <TemplateContent>  
    <Project File="ProjectTemplate.csproj" ReplaceParameters="true">  
      <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>  
      <ProjectItem ReplaceParameters="true" OpenInEditor="true">Class1.cs</ProjectItem>  
    </Project>  
  </TemplateContent>  
</VSTemplate>  
  
```  
  
 Ecco il file con estensione vstman (è possibile trovarlo nella directory del manifesto del progetto VSIX) che è il risultato della ricompilazione del progetto VSIX:  
  
```  
VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
  <VSTemplateContainer TemplateType="Project">  
    <RelativePathOnDisk>CSharp\1033\ProjectTemplate1</RelativePathOnDisk>  
    <TemplateFileName>ProjectTemplate1.vstemplate</TemplateFileName>  
    <VSTemplateHeader>  
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <Name>ProjectTemplate1</Name>  
        <Description>ProjectTemplate1</Description>  
        <Icon>ProjectTemplate1.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
        <SortOrder>1000</SortOrder>  
        <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>  
        <CreateNewFolder>true</CreateNewFolder>  
        <DefaultName>ProjectTemplate1</DefaultName>  
        <ProvideDefaultName>true</ProvideDefaultName>  
      </TemplateData>  
    </VSTemplateHeader>  
  </VSTemplateContainer>  
</VSTemplateManifest>  
  
```  
  
 Le informazioni fornite per il [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) elemento rimane invariato. Il  **\<VSTemplateContainer >** elemento punta al file con estensione vstemplate per il modello associato.  
  
 Ecco il file con estensione vstemplate di elemento predefinito creato da Visual Studio 2015:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">  
  <TemplateData>  
    <Name>ItemTemplate1</Name>  
    <Description>ItemTemplate1</Description>  
    <Icon>ItemTemplate1.ico</Icon>  
    <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>  
    <ProjectType>CSharp</ProjectType>  
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
    <DefaultName>Class.cs</DefaultName>  
  </TemplateData>  
  <TemplateContent>  
    <References>  
      <Reference>  
        <Assembly>System</Assembly>  
      </Reference>  
    </References>  
    <ProjectItem ReplaceParameters="true">Class.cs</ProjectItem>  
  </TemplateContent>  
</VSTemplate>  
  
```  
  
 Ecco il file con estensione vstman (è possibile trovarlo nella directory del manifesto del progetto VSIX) che è il risultato della ricompilazione del progetto VSIX:  
  
```  
VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
  <VSTemplateContainer TemplateType="Item">  
    <RelativePathOnDisk>CSharp\1033\ItemTemplate1</RelativePathOnDisk>  
    <TemplateFileName>ItemTemplate1.vstemplate</TemplateFileName>  
    <VSTemplateHeader>  
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <Name>ItemTemplate1</Name>  
        <Description>ItemTemplate1</Description>  
        <Icon>ItemTemplate1.ico</Icon>  
        <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>  
        <ProjectType>CSharp</ProjectType>  
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
        <DefaultName>Class.cs</DefaultName>  
      </TemplateData>  
    </VSTemplateHeader>  
  </VSTemplateContainer>  
</VSTemplateManifest>  
  
```  
  
 Le informazioni fornite per il  **\<TemplateData >** elemento rimane invariato. Il  **\<VSTemplateContainer >** elemento punta al file con estensione vstemplate per il modello associato  
  
 Per altre informazioni sui diversi elementi del file con estensione vstman, vedere [Visual Studio modello Manifest Schema Reference](../extensibility/visual-studio-template-manifest-schema-reference.md).  
  
## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Gli aggiornamenti per le estensioni installate con un. IDENTITÀ DEL SERVIZIO GESTITO  
 Alcune estensioni basate su MSI distribuire modelli in posizioni di modelli comuni, ad esempio il seguente:  
  
-   **\<Directory di installazione di Visual Studio > \Common7\IDE.\\< ProjectTemplates/ItemTemplates >**  
  
-   **\<Directory di installazione di Visual Studio > \Common7\IDE\Extensions\\< ExtensionName\>\\< progetto/ItemTemplates >**  
  
 Se l'estensione esegue una distribuzione basata su MSI, è necessario generare manualmente il manifesto di modello e assicurarsi che sia incluso nel programma di installazione di estensione. È necessario confrontare gli esempi con estensione vstman elencati in precedenza e il [Visual Studio modello Manifest Schema Reference](../extensibility/visual-studio-template-manifest-schema-reference.md). Per vedere cosa è necessario includere  
  
 È consigliabile creare manifesti distinti per i modelli di progetto ed elemento e puntano a root directory del modello come specificato sopra. È consigliabile creare un manifesto per ogni estensione e le impostazioni locali.  
  
## <a name="troubleshooting-template-installation"></a>Risoluzione dei problemi di installazione del modello  
 Se si verificano problemi relativi alla distribuzione dei modelli di progetto o un elemento, è possibile abilitare la registrazione diagnostica.  
  
1.  Eseguire il comando seguente per impostare la chiave del Registro di sistema per abilitare la registrazione:  
  
     **REG aggiungere HKCU\software\microsoft\visualstudio\15.0_Config\VSTemplate /v EnableTemplateDiscoveryLog /t REG_DWORD /d 1**  
  
2.  Avviare Visual Studio e avviare le finestre di dialogo Nuovo progetto e nuovo elemento per inizializzare entrambi gli alberi di modello. Il log di modello viene visualizzato nel **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0\VsTemplateDiagnosticsList.csv**. Ogni inizializzazione di struttura ad albero del modello aggiunge voci al log.  
  
 Il file di log contiene le colonne seguenti:  
  
-   **FullPathToTemplate**, che presenta i seguenti valori:  
  
    -   1 per la distribuzione basata su manifesto  
  
    -   0 per la distribuzione basata su disco  
  
-   **TemplateFileName**  
  
-   Altre proprietà del modello


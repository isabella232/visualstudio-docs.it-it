---
title: Aggiornare modelli di progetto ed elemento personalizzati per Visual Studio 2017Upgrade custom project and item templates for Visual Studio 2017
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 5f807e142b376d05e5a44600e8f6b24ddb3593be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698852"
---
# <a name="upgrade-custom-project-and-item-templates-for-visual-studio-2017"></a>Aggiornare modelli di progetto e di elemento personalizzati per Visual Studio 2017Upgrade Custom Project and Item Templates for Visual Studio 2017

A partire da Visual Studio 2017, Visual Studio individua i modelli di progetto e di elemento che sono stati installati da un vsix o un file msi in modo diverso dalle versioni precedenti di Visual Studio. Se possiedi estensioni che usano modelli di progetto o di elemento personalizzati, devi aggiornare le estensioni. Questo articolo spiega cosa è necessario fare.

Questa modifica ha effetto solo su Visual Studio 2017.This change affects only Visual Studio 2017. Non influisce sulle versioni precedenti di Visual Studio.

Se si desidera creare un modello di progetto o di elemento come parte di un'estensione VSIX, vedere Creazione di modelli di [progetto e di elemento personalizzati](../extensibility/creating-custom-project-and-item-templates.md).

## <a name="template-scanning"></a>Scansione dei modelli

Nelle versioni precedenti di Visual Studio, **devenv /setup** o **devenv /installvstemplates** analizzava il disco locale per trovare modelli di progetto e di elemento. A partire da Visual Studio 2017, l'analisi viene eseguita solo per la posizione a livello utente. Il percorso predefinito a livello di utente è **%USERPROFILE%,\\ Documenti<versione\>di Visual Studio, modelli\\**. Questo percorso viene utilizzato per i modelli generati dal comando Modelli di > **esportazione** **progetto...** se l'opzione **Importa automaticamente il modello in Visual Studio** è selezionata nella procedura guidata.

Per altri percorsi (non utente), è necessario includere un file manifesto (con estensione vstman) che specifica il percorso e altre caratteristiche del modello. Il file .vstman viene generato insieme al file .vstemplate utilizzato per i modelli. Se si installa l'estensione utilizzando un vsix, è possibile eseguire questa operazione ricompilando l'estensione in Visual Studio 2017.If you install your extension using a .vsix, you can accomplish this by recompiling the extension in Visual Studio 2017. Ma se si utilizza un file con estensione msi, è necessario apportare le modifiche manualmente. Per un elenco delle operazioni da eseguire per apportare queste modifiche, vedere **Aggiornamenti per le estensioni installate con un file . MSI** più avanti in questa pagina.

## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Come aggiornare un'estensione VSIX con modelli di progetto o elementoHow to Update a VSIX Extension with Project or Item Templates

1. Aprire la soluzione in Visual Studio 2017.Open the solution in Visual Studio 2017. Ti verrà chiesto di aggiornare il codice. Fare clic su **OK**.

2. Al termine dell'aggiornamento, potrebbe essere necessario modificare la versione della destinazione di installazione. Nel progetto VSIX aprire il file source.extension.vsixmanifest e selezionare la scheda **Installa destinazioni.** Se il campo **Intervallo** versioni è **[14.0],** fare clic su **Modifica** e modificarlo per includere Visual Studio 2017. Ad esempio, è possibile impostarlo su **[14.0,15.0]** per installare l'estensione su Visual Studio 2015 o Visual Studio 2017 o su **[15.0]** per installarlo solo in Visual Studio 2017.

3. Ricompilare il codice.

4. Chiudere Visual Studio.

5. Installare il valore VSIX.

6. È possibile testare l'aggiornamento eseguendo le operazioni seguenti:You can test the update by doing the following:

    1. La modifica dell'analisi dei file viene attivata dalla seguente chiave del Registro di sistema:

         **reg aggiungere hklm software microsoft Visualstudio 15.0 VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**

    2. Dopo aver aggiunto la chiave, eseguire **devenv /installvstemplates**.

    3. Riaprire Visual Studio. Il modello dovrebbe essere trovato nella posizione prevista.

    > [!NOTE]
    > I modelli di progetto di estensibilità di Visual Studio non sono disponibili quando è presente la chiave del Registro di sistema. È necessario eliminare la chiave del Registro di sistema (ed eseguire nuovamente **devenv /installvstemplates**) per utilizzarli.

## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Altri suggerimenti per la distribuzione di modelli di progetto e di elementoOther Recommendations for Deploying Project and Item Templates

- Evitare di utilizzare file di modello compressi. I file di modello compressi devono essere decompressi per recuperare risorse e contenuti, in modo che siano più costosi da utilizzare. È invece consigliabile distribuire i modelli di progetto ed elemento come singoli file nella propria directory per velocizzare l'inizializzazione del modello. Per le estensioni VSIX, le attività di compilazione SDK decomprimeranno automaticamente qualsiasi modello compresso durante la creazione del file VSIX.

- Evitare di usare le voci dell'ID pacchetto/risorsa per il nome del modello, la descrizione, l'icona o l'anteprima per evitare carichi di assembly di risorse non necessari durante l'individuazione del modello. Al contrario, è possibile usare i manifesti localizzati per creare una voce di modello per ogni impostazione locale, che usa nomi o proprietà localizzati.

- Se si includono modelli come elementi di file, la generazione del manifesto potrebbe non fornire i risultati previsti. In tal caso, sarà necessario aggiungere un manifesto generato manualmente al progetto VSIX.

## <a name="file-changes-in-project-and-item-templates"></a>File Changes in Project and Item Templates
Vengono illustrati i punti di differenza tra le versioni di Visual Studio 2015 e Visual Studio 2017 dei file di modello, in modo che è possibile creare correttamente i nuovi file.

 Di seguito è riportato il file con estensione vstemplate del progetto predefinito creato da Visual Studio 2015:Here is the default project .vstemplate file created by Visual Studio 2015:

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

 Ecco il file con estensione vstman (è possibile trovarlo nella directory manifesto del progetto VSIX) risultante dalla ricostruzione del progetto VSIX:

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
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

 Le informazioni fornite dall'elemento [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) rimangono invariate. Il ** \<VSTemplateContainer>** elemento punta al file .vstemplate per il modello associato.

 Di seguito è riportato l'elemento predefinito .vstemplate file creato da Visual Studio 2015:Here is the default item .vstemplate file created by Visual Studio 2015:

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

 Ecco il file con estensione vstman (è possibile trovarlo nella directory manifesto del progetto VSIX) risultante dalla ricostruzione del progetto VSIX:

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
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

 Le informazioni fornite dall'elemento ** \<>TemplateData** rimangono invariate. L'elemento ** \<>VSTemplateContainer** punta al file .vstemplate per il modello associato

 Per ulteriori informazioni sui diversi elementi del file vstman , vedere Riferimenti allo [schema del manifesto](../extensibility/visual-studio-template-manifest-schema-reference.md)del modello di Visual Studio .

## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Aggiornamenti per le estensioni installate con un file . Msi

Alcune estensioni basate su MSI distribuiscono modelli in percorsi di modelli comuni, ad esempio le directory seguenti:

- **\<Directory di installazione di Visual Studio\\>,Common7,IDE<ProjectTemplates/ItemTemplates\>**

- **\<Directory di installazione di Visual Studio>'>, Common7, IDE, Estensioni\\<NomeEstensione\> \\<Project/ItemTemplates\>**

Se l'estensione esegue una distribuzione basata su MSI, è necessario generare manualmente il manifesto del modello e assicurarsi che sia incluso nella configurazione dell'estensione. Confrontare gli esempi con estensione vstman elencati in precedenza e la Guida di riferimento allo [schema del manifesto](../extensibility/visual-studio-template-manifest-schema-reference.md)del modello di Visual Studio .

Creare manifesti separati per i modelli di progetto e di elemento e devono puntare alla directory dei modelli radice come specificato in precedenza. Creare un manifesto per estensione e impostazioni locali.

## <a name="see-also"></a>Vedere anche

- [Risoluzione dei problemi relativi all'individuazione dei modelliTroubleshooting](troubleshooting-template-discovery.md)
- [Creazione di modelli di progetto e di elemento personalizzati](creating-custom-project-and-item-templates.md)

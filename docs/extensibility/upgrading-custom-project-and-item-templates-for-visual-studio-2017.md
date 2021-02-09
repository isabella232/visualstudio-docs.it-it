---
title: Aggiornare i modelli di progetto e di elemento personalizzati per Visual Studio 2017
titleSuffix: ''
description: Informazioni su come aggiornare il progetto e il modello di elemento personalizzati da versioni precedenti di Visual Studio SDK per l'uso con Visual Studio 2017 e versioni successive.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 84e9b08350cf5977269bfbcf28ca5335e17f024d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893405"
---
# <a name="upgrade-custom-project-and-item-templates-for-visual-studio-2017"></a>Aggiornare Modelli di progetti ed elementi per Visual Studio personalizzati 2017

A partire da Visual Studio 2017, Visual Studio individua i modelli di progetti e di elementi che sono stati installati da un file con estensione VSIX o MSI in modo diverso per le versioni precedenti di Visual Studio. Se si possiedono estensioni che usano modelli di progetto o di elemento personalizzati, è necessario aggiornare le estensioni. Questo articolo spiega cosa è necessario fare.

Questa modifica ha effetto solo su Visual Studio 2017. Non influisce sulle versioni precedenti di Visual Studio.

Se si vuole creare un modello di progetto o di elemento come parte di un'estensione VSIX, vedere [creazione di modelli di progetto e di elemento personalizzati](../extensibility/creating-custom-project-and-item-templates.md).

## <a name="template-scanning"></a>Analisi dei modelli

Nelle versioni precedenti di Visual Studio, **devenv/setup** o **devenv/installvstemplates** ha analizzato il disco locale per trovare i modelli di progetto e di elemento. A partire da Visual Studio 2017, l'analisi viene eseguita solo per la posizione a livello di utente. Il percorso predefinito a livello di utente è **%userprofile%\documenti \\<Visual Studio \> versione \\ \Modelli**. Questo percorso viene usato per i modelli generati dal   >  comando **Esporta modelli** di progetto... se l'opzione **Importa automaticamente il modello in Visual Studio** è selezionata nella procedura guidata.

Per altri percorsi (non utente), è necessario includere un file manifesto (con estensione vstman) che specifichi il percorso e altre caratteristiche del modello. Il file con estensione vstman viene generato insieme al file con estensione vstemplate utilizzato per i modelli. Se si installa l'estensione usando un. vsix, è possibile eseguire questa operazione ricompilando l'estensione in Visual Studio 2017. Tuttavia, se si usa un file con estensione msi, è necessario apportare manualmente le modifiche. Per un elenco delle operazioni necessarie per apportare queste modifiche, vedere  **aggiornamenti per le estensioni installate con un. MSI** più avanti in questa pagina.

## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Come aggiornare un'estensione VSIX con i modelli di progetto o di elemento

1. Aprire la soluzione in Visual Studio 2017. Verrà richiesto di aggiornare il codice. Fare clic su **OK**.

2. Al termine dell'aggiornamento, potrebbe essere necessario modificare la versione della destinazione di installazione. Nel progetto VSIX aprire il file source. Extension. vsixmanifest e selezionare la scheda **destinazioni di installazione** . Se il campo **intervallo di versioni** è **[14,0]**, fare clic su **modifica** e modificarlo in modo da includere Visual Studio 2017. Ad esempio, è possibile impostarlo su **[14.0, 15.0]** per installare l'estensione in visual studio 2015 o visual studio 2017 o in **[15,0]** per installarlo solo in Visual Studio 2017.

3. Ricompilare il codice.

4. Chiudere Visual Studio.

5. Installare il progetto VSIX.

6. È possibile testare l'aggiornamento eseguendo le operazioni seguenti:

    1. La modifica dell'analisi dei file viene attivata dalla seguente chiave del registro di sistema:

         **reg add hklm\software\microsoft\visualstudio\15.0\VSTemplate/v DisableTemplateScanning/t REG_DWORD/d 1/reg: 32**

    2. Dopo aver aggiunto la chiave, eseguire **devenv/installvstemplates**.

    3. Riaprire Visual Studio. Il modello verrà trovato nel percorso previsto.

    > [!NOTE]
    > I modelli di progetto di estendibilità di Visual Studio non sono disponibili quando è presente la chiave del registro di sistema. Per usarli, è necessario eliminare la chiave del registro di sistema ed eseguire di nuovo **devenv/installvstemplates**.

## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Altri consigli per la distribuzione di modelli di progetti ed elementi

- Evitare l'uso di file di modello compressi. È necessario decomprimere i file di modello compressi per recuperare risorse e contenuto, in modo che siano su da usare. Al contrario, è necessario distribuire i modelli di progetto e di elemento come singoli file nella propria directory per velocizzare l'inizializzazione del modello. Per le estensioni VSIX, le attività di compilazione dell'SDK decomprimeranno automaticamente qualsiasi modello compresso durante la creazione del file VSIX.

- Evitare di usare voci di ID di pacchetto/risorsa per il nome del modello, la descrizione, l'icona o l'anteprima per evitare il caricamento di assembly di risorse non necessari durante l'individuazione del modello. È invece possibile usare manifesti localizzati per creare una voce di modello per ogni impostazione locale, che usa nomi o proprietà localizzate.

- Se si includono modelli come elementi di file, la generazione del manifesto potrebbe non fornire i risultati previsti. In tal caso, sarà necessario aggiungere un manifesto generato manualmente al progetto VSIX.

## <a name="file-changes-in-project-and-item-templates"></a>Modifiche ai file nei modelli di progetto e di elemento
Vengono mostrati i punti di differenza tra le versioni di Visual Studio 2015 e Visual Studio 2017 dei file modello, in modo che sia possibile creare correttamente i nuovi file.

 Ecco il file Project. vstemplate predefinito creato da Visual Studio 2015:

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

 Ecco il file. vstman (è possibile trovarlo nella directory del manifesto del progetto VSIX) risultante dalla ricompilazione del progetto VSIX:

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

 Le informazioni fornite dall'elemento [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) rimangono invariate. L' **\<VSTemplateContainer>** elemento fa riferimento al file con estensione vstemplate per il modello associato.

 Ecco il file con estensione vstemplate predefinito creato da Visual Studio 2015:

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

 Ecco il file. vstman (è possibile trovarlo nella directory del manifesto del progetto VSIX) risultante dalla ricompilazione del progetto VSIX:

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

 Le informazioni fornite dall' **\<TemplateData>** elemento rimangono invariate. L' **\<VSTemplateContainer>** elemento fa riferimento al file con estensione vstemplate per il modello associato

 Per altre informazioni sui diversi elementi del file con estensione vstman, vedere [riferimenti allo schema del manifesto del modello di Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Aggiornamenti per le estensioni installate con un. MSI

Alcune estensioni basate su MSI consentono di distribuire modelli in percorsi di modelli comuni, ad esempio le directory seguenti:

- **\<Visual Studio installation directory>\Common7\IDE \\<ProjectTemplates/ItemTemplates\>**

- **\<Visual Studio installation directory>\Common7\IDE\Extensions \\<extensionname \> \\<progetto/ItemTemplates\>**

Se l'estensione esegue una distribuzione basata su MSI, è necessario generare manualmente il manifesto del modello e verificare che sia incluso nella configurazione dell'estensione. Confrontare gli esempi. vstman elencati sopra e il [riferimento allo schema del manifesto del modello di Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

Creare manifesti distinti per i modelli di progetto e di elemento e devono puntare alla directory radice del modello, come specificato in precedenza. Creare un manifesto per estensione e impostazioni locali.

## <a name="see-also"></a>Vedi anche

- [Risoluzione dei problemi di individuazione dei modelli](troubleshooting-template-discovery.md)
- [Creazione di modelli di progetto e di elemento personalizzati](creating-custom-project-and-item-templates.md)

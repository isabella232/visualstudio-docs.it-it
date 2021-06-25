---
title: Aggiornare modelli di progetto ed elemento personalizzati per Visual Studio 2017
titleSuffix: ''
description: Informazioni su come aggiornare il progetto personalizzato e il modello di elemento dalle versioni precedenti di Visual Studio SDK per l'uso con Visual Studio 2017 e versioni successive.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 0d07af0a00ab840df8a9af437bcddc427f606948
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903060"
---
# <a name="upgrade-custom-project-and-item-templates-for-visual-studio-2017"></a>Aggiornare la versione Modelli di progetti ed elementi per Visual Studio 2017

A partire da Visual Studio 2017, Visual Studio individua i modelli di progetto ed elemento installati da un file con estensione vsix o da un .msi in modo diverso rispetto alle versioni precedenti di Visual Studio. Se si è proprietari di estensioni che usano modelli di progetto o di elemento personalizzati, è necessario aggiornare le estensioni. Questo articolo illustra le cose da fare.

Questa modifica interessa solo Visual Studio 2017. Non influisce sulle versioni precedenti di Visual Studio.

Se si vuole creare un modello di progetto o di elemento come parte di un'estensione VSIX, vedere Creazione di modelli di [progetto ed elementi personalizzati.](../extensibility/creating-custom-project-and-item-templates.md)

## <a name="template-scanning"></a>Analisi dei modelli

Nelle versioni precedenti di Visual Studio, **devenv /setup** o **devenv /installvstemplates** analizzava il disco locale per trovare i modelli di progetto ed elemento. A partire Visual Studio 2017, l'analisi viene eseguita solo per la posizione a livello di utente. Il percorso predefinito a livello di utente è **%USERPROFILE%\Documents \\<Visual Studio \> versione \Templates \\**. Questo percorso viene usato per i modelli generati dal comando Project Export Templates... (Esporta modelli di progetto), se l'opzione Automatically import the template into Visual Studio (Importa automaticamente il modello in Visual Studio)  >   è selezionata nella procedura guidata. 

Per altri percorsi (non utente), è necessario includere un file manifesto (con estensione vstman) che specifica il percorso e altre caratteristiche del modello. Il file con estensione vstman viene generato insieme al file con estensione vstemplate usato per i modelli. Se si installa l'estensione usando un file con estensione vsix, è possibile eseguire questa operazione ricompilando l'estensione in Visual Studio 2017. Tuttavia, se si usa un .msi, è necessario apportare le modifiche manualmente. Per un elenco delle operazioni da eseguire per apportare queste modifiche, vedere  **Upgrades for Extensions Installed with an .MSI** più avanti in questa pagina.

## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Come aggiornare un'estensione VSIX con modelli di progetto o di elemento

1. Aprire la soluzione in Visual Studio 2017. Verrà richiesto di aggiornare il codice. Fare clic su **OK**.

2. Al termine dell'aggiornamento, potrebbe essere necessario modificare la versione della destinazione di installazione. Nel progetto VSIX aprire il file source.extension.vsixmanifest e selezionare la **scheda Destinazioni di** installazione. Se il **campo Intervallo** di versioni **è [14.0]**, fare clic su Modifica e modificarlo per includere Visual Studio 2017.  Ad esempio, è possibile impostarla su **[14.0,15.0]** per installare l'estensione in Visual Studio 2015 o Visual Studio 2017 o su **[15.0]** per installarla solo Visual Studio 2017.

3. Ricompilare il codice.

4. Chiudere Visual Studio.

5. Installare VSIX.

6. È possibile testare l'aggiornamento eseguendo le operazioni seguenti:

    1. La modifica di analisi dei file viene attivata dalla chiave del Registro di sistema seguente:

         **reg add hklm\software\microsoft\visualstudio\15.0\VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**

    2. Dopo aver aggiunto la chiave, eseguire **devenv /installvstemplates**.

    3. Riaprire Visual Studio. Il modello dovrebbe essere presente nel percorso previsto.

    > [!NOTE]
    > I Visual Studio di progetto di estendibilità non sono disponibili quando è presente la chiave del Registro di sistema. È necessario eliminare la chiave del Registro di sistema e **rieseguire devenv /installvstemplates** per usarle.

## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Altri consigli per la distribuzione di modelli di progetto ed elemento

- Evitare di usare file modello compressi. I file modello compressi devono essere decompressi per recuperare risorse e contenuto, quindi saranno più costosi da usare. È invece consigliabile distribuire i modelli di progetto ed elemento come singoli file nella propria directory per velocizzare l'inizializzazione dei modelli. Per le estensioni VSIX, le attività di compilazione dell'SDK decomprimeranno automaticamente qualsiasi modello compresso durante la creazione del file VSIX.

- Evitare di usare voci di ID pacchetto/risorsa per il nome del modello, la descrizione, l'icona o l'anteprima per evitare caricamenti di assembly di risorse non necessari durante l'individuazione del modello. È invece possibile usare manifesti localizzati per creare una voce di modello per ogni impostazione locale, che usa nomi o proprietà localizzati.

- Se si includono modelli come elementi di file, la generazione del manifesto potrebbe non fornire i risultati previsti. In tal caso, sarà necessario aggiungere un manifesto generato manualmente al progetto VSIX.

## <a name="file-changes-in-project-and-item-templates"></a>Modifiche ai file nei modelli di progetto e di elemento
Vengono mostrati i punti di differenza tra le versioni Visual Studio 2015 e Visual Studio 2017 dei file modello, in modo da poter creare correttamente i nuovi file.

 Ecco il file con estensione vstemplate del progetto predefinito creato da Visual Studio 2015:

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

 Ecco il file con estensione vstman (disponibile nella directory del manifesto del progetto VSIX) che ha generato la ricompilazione del progetto VSIX:

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

 Le informazioni fornite [dall'elemento TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) rimangono invariate. **\<VSTemplateContainer>** L'elemento punta al file con estensione vstemplate per il modello associato.

 Ecco il file con estensione vstemplate dell'elemento predefinito creato Visual Studio 2015:

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

 Ecco il file con estensione vstman (disponibile nella directory del manifesto del progetto VSIX) che ha generato la ricompilazione del progetto VSIX:

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

 Le informazioni fornite **\<TemplateData>** dall'elemento rimangono invariate. **\<VSTemplateContainer>** L'elemento punta al file con estensione vstemplate per il modello associato

 Per altre informazioni sui diversi elementi del file con estensione vstman, vedere Visual Studio schema del [manifesto del modello.](../extensibility/visual-studio-template-manifest-schema-reference.md)

## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Aggiornamenti per le estensioni installate con un .MSI

Alcune estensioni basate su MSI distribuiscono modelli in percorsi di modelli comuni, ad esempio le directory seguenti:

- **\<Visual Studio installation directory>\Common7\IDE \\<ProjectTemplates/ItemTemplates\>**

- **\<Visual Studio installation directory>\Common7\IDE\Extensions \\<ExtensionName \> \\<Project/ItemTemplates\>**

Se l'estensione esegue una distribuzione basata su MSI, è necessario generare manualmente il manifesto del modello e assicurarsi che sia incluso nella configurazione dell'estensione. Confrontare gli esempi con estensione vstman elencati in precedenza e le informazioni di Visual Studio schema del manifesto [del modello.](../extensibility/visual-studio-template-manifest-schema-reference.md)

Creare manifesti separati per i modelli di progetto ed elemento e devono puntare alla directory radice del modello come specificato in precedenza. Creare un manifesto per estensione e impostazioni locali.

## <a name="see-also"></a>Vedere anche

- [Risoluzione dei problemi di individuazione dei modelli](troubleshooting-template-discovery.md)
- [Creazione di modelli di progetto ed elemento personalizzati](creating-custom-project-and-item-templates.md)

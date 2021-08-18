---
title: Localizzazione di pacchetti VSIX | Microsoft Docs
description: Informazioni su come localizzare un pacchetto VSIX creando un file Extension.vsixlangpack per ogni linguaggio di destinazione e inserendoli nella cartella corretta.
ms.custom: SEO-VS-2020
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c818c05831f48875c1ad15c47d3d5f3c1610997e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122152224"
---
# <a name="localizing-vsix-packages"></a>Localizzazione di pacchetti VSIX

È possibile localizzare un pacchetto VSIX creando un file *Extension.vsixlangpack* per ogni linguaggio di destinazione e inserendoli nella cartella corretta. Quando viene installato un pacchetto localizzato, il nome localizzato dell'estensione viene visualizzato insieme a una descrizione localizzata. Se si specifica un file di licenza localizzato o un URL che punta alle informazioni localizzate, vengono visualizzati anche questi file.

Se il contenuto del pacchetto VSIX include un PACCHETTO VSPackage che aggiunge comandi di menu o un'altra interfaccia utente, vedere [Localizzare](../extensibility/localizing-menu-commands.md) i comandi di menu per informazioni sulla localizzazione dei nuovi elementi dell'interfaccia utente.

## <a name="directory-structure"></a>Struttura di directory

 Quando un utente installa un'estensione, **estensioni** e aggiornamenti controlla il livello superiore del pacchetto VSIX per una cartella il cui nome corrisponde alle impostazioni locali Visual Studio del computer di destinazione. Se **Extensions and Updates** trova un file con estensione *vsixlangpack* nella cartella , sostituisce i valori localizzati in tale file con i valori corrispondenti nel file con estensione *vsixmanifest.* Questi valori vengono visualizzati durante l'installazione dell'estensione. L'esempio seguente illustra la struttura di directory per un pacchetto VSIX localizzato in spagnolo (es-ES) e francese (fr-FR).

```text
.
├── MyExtension.dll
├── Extension.vsixmanifest
├── [Content_Types].xml
├── es-ES
│   └── Extension.vsixlangpack
└── fr-FR
    └── Extension.vsixlangpack
```

> [!NOTE]
> I modelli di progetto supportati da VSIX in generano un manifesto VSIX e [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] denomano il file *source.extension.vsixmanifest.* Quando Visual Studio compila il progetto, copia il contenuto del file in Extension.VsixManifest nel pacchetto VSIX.

## <a name="the-extensionvsixlangpack-file"></a>File Extension.vsixlangpack

Il file *Extension.vsixlangpack* segue lo [schema del Language Pack VSIX 2.0.](../extensibility/vsix-language-pack-schema-2-0-reference.md) Questo schema ha un `PackageLanguagePackManifest` oggetto , che è immediatamente seguito da un elemento `Metadata` figlio. L'elemento Metadata può contenere fino a 6 elementi figlio, `DisplayName` , , , , e `Description` `MoreInfo` `License` `ReleaseNotes` `Icon` . Questi elementi figlio corrispondono agli elementi figlio , , , , e dell'elemento `DisplayName` `Description` del file `MoreInfo` `License` `ReleaseNotes` `Icon` `Metadata` *Extension.vsixmanifest.*

Quando si crea un file vsixlangpack, è necessario impostare la `Include in Vsix` proprietà su `true` . In caso contrario, il testo di installazione localizzato verrà ignorato.

### <a name="to-set-the-include-in-vsix-property"></a>Per impostare la proprietà Include in Vsix

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul file Extension.vsixlangpack e quindi **scegliere Proprietà.**

2. In **Griglia delle proprietà fare** clic **su Includi in Vsix** e impostarne il valore su `true` .

## <a name="example"></a>Esempio

### <a name="description"></a>Descrizione

L'esempio seguente mostra le parti pertinenti di un file *Extension.vsixmanifest.* Il file include anche il file *Extension.vsixlangpack corrispondente* per lo spagnolo. I valori dell'language pack sostituiscono i valori del manifesto se le impostazioni Visual Studio locali del computer di destinazione sono impostate su spagnolo.

### <a name="code"></a>Codice

- [*Extension.vsixmanifest*]

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageManifest ...>
  <Metadata ...>
    <DisplayName>Family Tree</DisplayName>
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>
    <MoreInfo>http://www.contoso.com/products/FamilyTree.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
  <Installation .../>
  <Dependencies .../>
  <Prerequisites .../>
  <Assets .../>
</PackageManifest>
```

- [*Extension.vsixlangpack*]

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageLanguagePackManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <DisplayName>Arbol de Familia</DisplayName>
    <Description> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</Description>
    <MoreInfo> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
</PackageLanguagePackManifest>
```

## <a name="see-also"></a>Vedi anche

|Titolo|Descrizione|
|-----------|-----------------|
|[Informazioni di riferimento sullo schema del Language Pack VSIX 2.0](vsix-language-pack-schema-2-0-reference.md)|Un language pack VSIX descrive le informazioni di localizzazione di un file di distribuzione vsix.|
|[Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Descrive la struttura e il contenuto di un pacchetto vsix.|
|[Comandi di menu Localizza](../extensibility/localizing-menu-commands.md)|Illustra come localizzare altre risorse di testo in un'estensione.|

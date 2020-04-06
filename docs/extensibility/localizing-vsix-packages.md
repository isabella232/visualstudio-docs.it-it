---
title: Localizzazione di pacchetti VSIX Documenti Microsoft
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d2d4222e45d56447951e86d558af9983a0d1cc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702892"
---
# <a name="localizing-vsix-packages"></a>Localizzazione di pacchetti VSIX

È possibile localizzare un pacchetto VSIX creando un file *Extension.vsixlangpack* per ogni lingua di destinazione e quindi inserendoli nella cartella corretta. Quando viene installato un pacchetto localizzato, il nome localizzato dell'estensione viene visualizzato insieme a una descrizione localizzata. Se si fornisce un file di licenza localizzato o un URL che punta a informazioni localizzate, vengono visualizzate anche queste informazioni.

Se il contenuto del pacchetto VSIX include un pacchetto VSPackage che aggiunge comandi di menu o un'altra interfaccia utente, vedere [localizzare i comandi](../extensibility/localizing-menu-commands.md) di menu per informazioni sulla localizzazione dei nuovi elementi dell'interfaccia utente.

## <a name="directory-structure"></a>Struttura di directory

 Quando un utente installa un'estensione, **estensioni e aggiornamenti** controlla il livello superiore del pacchetto VSIX per una cartella il cui nome corrisponde alle impostazioni locali di Visual Studio del computer di destinazione. Se **Extensions and Updates** trova un file con estensione *vsixlangpack* nella cartella, sostituisce i valori localizzati in tale file con i valori corrispondenti nel file *con estensione vsixmanifest.* Questi valori vengono visualizzati durante l'installazione dell'estensione. Nell'esempio seguente viene illustrata la struttura di directory per un pacchetto VSIX localizzato in spagnolo (es-ES) e francese (fr-FR).

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
> I modelli di progetto supportati [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] da VSIX nel generare un manifesto VSIX e denominarlo *source.extension.vsixmanifest*. Quando Visual Studio compila il progetto, copia il contenuto di tale file in Extension.VsixManifest nel pacchetto VSIX.

## <a name="the-extensionvsixlangpack-file"></a>Il file Extension.vsixlangpack

Il file *Extension.vsixlangpack* segue [lo schema 2.0 del Language Pack VSIX.](../extensibility/vsix-language-pack-schema-2-0-reference.md) Questo schema `PackageLanguagePackManifest`ha un oggetto , `Metadata` seguito immediatamente da un elemento figlio. L'elemento Metadata può contenere `DisplayName`fino `Description` `MoreInfo`a `License` `ReleaseNotes`6 `Icon`elementi figlio, , , , , , e . Questi elementi figlio corrispondono `MoreInfo` `License`agli `ReleaseNotes`elementi `Icon` `DisplayName`, `Description`, `Metadata` , , e agli elementi figlio dell'elemento del file *Extension.vsixmanifest.*

Quando si crea un file vsixlangpack `Include in Vsix` , `true`è necessario impostare la proprietà su . In caso contrario, il testo di installazione localizzato verrà ignorato.

### <a name="to-set-the-include-in-vsix-property"></a>Per impostare la proprietà Include in Vsix

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul file Extension.vsixlangpack , quindi **scegliere Proprietà**.

2. Nella **griglia delle proprietà**, fare clic su `true`Includi in **Vsix**e impostarne il valore su .

## <a name="example"></a>Esempio

### <a name="description"></a>Descrizione

Nell'esempio seguente vengono illustrate le parti rilevanti di un file *Extension.vsixmanifest.* Il file include anche il file *Extension.vsixlangpack* corrispondente per lo spagnolo. I valori del Language Pack sostituiscono i valori del manifesto se le impostazioni locali di Visual Studio del computer di destinazione sono impostate su Spagnolo.

### <a name="code"></a>Codice

- [*Estensione.vsixmanifest*]

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

## <a name="see-also"></a>Vedere anche

|Titolo|Descrizione|
|-----------|-----------------|
|[Riferimento allo schema 2.0 del Language Pack VSIX](vsix-language-pack-schema-2-0-reference.md)|Un Language Pack VSIX descrive le informazioni di localizzazione di un file di distribuzione VSIX.|
|[Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Descrive la struttura e il contenuto di un pacchetto Vsix.|
|[Localizzare i comandi di menu](../extensibility/localizing-menu-commands.md)|Viene illustrato come localizzare altre risorse di testo in un'estensione.|

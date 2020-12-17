---
title: Localizzazione di pacchetti VSIX | Microsoft Docs
description: Informazioni su come localizzare un pacchetto VSIX creando un file Extension. vsixlangpack per ogni lingua di destinazione e inserendoli nella cartella corretta.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: cc9f7055145748e0625788e7487bb978911bae7f
ms.sourcegitcommit: d485b18e46ec4cf08704b5a8d0657bc716ec8393
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/17/2020
ms.locfileid: "97615538"
---
# <a name="localizing-vsix-packages"></a>Localizzazione di pacchetti VSIX

È possibile localizzare un pacchetto VSIX creando un file con *estensione vsixlangpack* per ogni lingua di destinazione e inserendoli nella cartella corretta. Quando viene installato un pacchetto localizzato, il nome localizzato dell'estensione viene visualizzato insieme a una descrizione localizzata. Se si fornisce un file di licenza localizzato o un URL che punta alle informazioni localizzate, vengono visualizzati anche.

Se il contenuto del pacchetto VSIX include un VSPackage che aggiunge comandi di menu o altra interfaccia utente, vedere [comandi di menu Localize](../extensibility/localizing-menu-commands.md) per informazioni sulla localizzazione dei nuovi elementi dell'interfaccia utente.

## <a name="directory-structure"></a>Struttura di directory

 Quando un utente installa un'estensione, le **estensioni e gli aggiornamenti** controllano il livello principale del pacchetto VSIX per una cartella il cui nome corrisponde alle impostazioni locali di Visual Studio del computer di destinazione. Se **estensioni e aggiornamenti** individuano un file con *estensione vsixlangpack* nella cartella, sostituisce i valori localizzati nel file per i valori corrispondenti nel file con *estensione vsixmanifest* . Questi valori vengono visualizzati quando si installa l'estensione. Nell'esempio seguente viene illustrata la struttura di directory per un pacchetto VSIX localizzato in spagnolo (es-ES) e francese (fr-FR).

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
> I modelli di progetto supportati da VSIX nell'oggetto [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] generano un manifesto VSIX e ne assegnano il nome *source. Extension. vsixmanifest*. Quando Visual Studio compila il progetto, copia il contenuto del file in Extension. VsixManifest nel pacchetto VSIX.

## <a name="the-extensionvsixlangpack-file"></a>Il file Extension. vsixlangpack

Il file *Extension. vsixlangpack* segue lo [schema del Language Pack VSIX 2,0](../extensibility/vsix-language-pack-schema-2-0-reference.md). Questo schema include un oggetto `PackageLanguagePackManifest` , che è immediatamente seguito da un `Metadata` elemento figlio. L'elemento Metadata può contenere fino a sei elementi figlio,,, `DisplayName` `Description` `MoreInfo` , `License` , `ReleaseNotes` e `Icon` . Questi elementi figlio corrispondono agli `DisplayName` `Description` elementi figlio,,, `MoreInfo` `License` , `ReleaseNotes` e `Icon` dell' `Metadata` elemento del file *Extension. vsixmanifest* .

Quando si crea un file vsixlangpack, è necessario impostare la `Include in Vsix` proprietà su `true` . In caso contrario, il testo di installazione localizzato verrà ignorato.

### <a name="to-set-the-include-in-vsix-property"></a>Per impostare la proprietà Includi in VSIX

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul file Extension. vsixlangpack, quindi scegliere **Proprietà**.

2. Nella **griglia delle proprietà** fare clic su **Includi in VSIX** e impostare il relativo valore su `true` .

## <a name="example"></a>Esempio

### <a name="description"></a>Descrizione

Nell'esempio seguente vengono illustrate le parti pertinenti di un file con *estensione vsixmanifest* . Il file include anche il file con *estensione vsixlangpack* corrispondente per lo spagnolo. I valori del Language Pack sostituiscono i valori del manifesto se le impostazioni locali di Visual Studio del computer di destinazione sono impostate su spagnolo.

### <a name="code"></a>Codice

- [*Estensione. vsixmanifest*]

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

- [*Estensione. vsixlangpack*]

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
|[Informazioni di riferimento sullo schema del Language Pack VSIX 2,0](vsix-language-pack-schema-2-0-reference.md)|Un Language Pack VSIX descrive le informazioni di localizzazione di un file di distribuzione con estensione VSIX.|
|[Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Descrive la struttura e il contenuto di un pacchetto VSIX.|
|[Comandi di menu Localize](../extensibility/localizing-menu-commands.md)|Viene illustrato come localizzare altre risorse di testo in un'estensione.|

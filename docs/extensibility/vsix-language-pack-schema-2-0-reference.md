---
title: Informazioni di riferimento sullo schema del Language Pack VSIX 2.0 | Microsoft Docs
description: Lo schema del Language Pack VSIX fornisce informazioni di installazione localizzate per i pacchetti VSIX. La versione 2.0 supporta elementi di localizzazione aggiuntivi.
ms.custom: SEO-VS-2020
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- language pack
- localize vsix
- localize package
- localize extension
ms.assetid: 2a2932bc-cdbe-4d32-91fa-a3e0474f9098
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.openlocfilehash: 8ade27ac47c25a3170c5c7c6048aa1c6c21181e4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122109890"
---
# <a name="vsix-language-pack-schema-20-reference"></a>Informazioni di riferimento sullo schema language pack VSIX 2.0

Lo schema del Language Pack VSIX fornisce informazioni di installazione localizzate per i pacchetti VSIX. La versione 2.0 di questo schema supporta elementi di localizzazione aggiuntivi.

## <a name="language-pack-schema"></a>Schema del Language Pack

L'elemento radice del file language pack è , con un attributo , che è la versione del language pack `<PackageLanguagePackManifest>` `Version` file. Questo articolo descrive la versione 2.0 del formato language pack, specificato nel manifesto impostando l'attributo `Version` sul valore `Version="2.0.0"` . L'elemento radice contiene esattamente un elemento `<Metadata>` figlio.

### <a name="packagelanguagepackmanifest-element"></a>Elemento PackageLanguagePackManifest

`<PackageLanguagePackManifest>`All'interno dell'elemento deve esistere l'elemento seguente:

|Titolo|Descrizione|
|-----------|-----------------|
|`<Metadata>`| Elemento contenitore per tutti i metadati del pacchetto localizzato

### <a name="metadata-element"></a>Elemento Metadata

`<Metadata>`All'interno dell'elemento è possibile avere gli elementi seguenti:

|Titolo|Descrizione|
|-----------|-----------------|
|`<DisplayName>`|Nome localizzato dell'estensione da installare|
|`<Description>`|Descrizione localizzata dell'estensione da installare|
|`<License>`| Percorso di una versione localizzata della licenza dell'estensione|
|`<MoreInfo>`| Collegamento alle informazioni localizzate sull'estensione|
|`<ReleaseNotes>`| Percorso o collegamento a una versione localizzata delle note sulla versione|
|`<Icon>`| Percorso di una versione localizzata dell'icona delle estensioni|

### <a name="sample-manifest"></a>Manifesto di esempio

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
|[Localizzazione di pacchetti VSIX](../extensibility/localizing-vsix-packages.md)|Viene illustrato come fornire supporto di installazione localizzato per un pacchetto VSIX.|
|[Informazioni di riferimento sullo schema dell'estensione VSIX 2.0](../extensibility/vsix-extension-schema-2-0-reference.md)|Un manifesto VSIX descrive il contenuto di un file *di distribuzione vsix.* Il file di distribuzione consente di installare un'estensione Visual Studio usando la finestra **di dialogo** Estensioni e aggiornamenti .|
|[Individuare e usare le estensioni di Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)|Illustra come usare la finestra **di dialogo** Estensioni e aggiornamenti per installare, rimuovere, attivare e disattivare le estensioni.|

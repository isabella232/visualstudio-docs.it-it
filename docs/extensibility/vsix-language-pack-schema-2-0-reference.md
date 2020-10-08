---
title: Informazioni di riferimento sullo schema del Language Pack VSIX 2,0 | Microsoft Docs
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- language pack
- localize vsix
- localize package
- localize extension
ms.assetid: 2a2932bc-cdbe-4d32-91fa-a3e0474f9098
author: acangialosi
ms.author: anthc
manager: jillfra
ms.openlocfilehash: f0eee51c0654c6e517209e23baf43c6b262d8f73
ms.sourcegitcommit: c31815e140f2ec79e00a9a9a19900778ec11e860
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/08/2020
ms.locfileid: "91830701"
---
# <a name="vsix-language-pack-schema-20-reference"></a>Informazioni di riferimento sullo schema del Language Pack VSIX 2,0

Lo schema del Language Pack VSIX fornisce informazioni di installazione localizzate per i pacchetti VSIX. La versione 2,0 di questo schema supporta elementi di localizzazione aggiuntivi.

## <a name="language-pack-schema"></a>Schema Language Pack

L'elemento radice del file di Language Pack è `<PackageLanguagePackManifest>` , con un attributo di `Version` , che è la versione del formato Language Pack. Questo articolo descrive la versione 2,0 del formato Language Pack, specificato nel manifesto impostando l' `Version` attributo sul valore `Version="2.0.0"` . L'elemento radice contiene esattamente un `<Metadata>` elemento figlio.

### <a name="packagelanguagepackmanifest-element"></a>Elemento PackageLanguagePackManifest

All'interno dell' `<PackageLanguagePackManifest>` elemento deve esistere l'elemento seguente:

|Titolo|Descrizione|
|-----------|-----------------|
|`<Metadata>`| Elemento contenitore per tutti i metadati del pacchetto localizzato

### <a name="metadata-element"></a>Elemento Metadata

All'interno dell' `<Metadata>` elemento è possibile avere gli elementi seguenti:

|Titolo|Descrizione|
|-----------|-----------------|
|`<DisplayName>`|Nome localizzato dell'estensione da installare|
|`<Description>`|Descrizione localizzata dell'estensione da installare|
|`<License>`| Percorso di una versione localizzata della licenza dell'estensione|
|`<MoreInfo>`| Collegamento alle informazioni localizzate sull'estensione|
|`<ReleaseNotes>`| Un percorso o un collegamento a una versione localizzata delle note sulla versione|
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

## <a name="see-also"></a>Vedere anche

|Titolo|Descrizione|
|-----------|-----------------|
|[Localizzazione di pacchetti VSIX](../extensibility/localizing-vsix-packages.md)|Viene illustrato come fornire supporto per l'installazione localizzata per un pacchetto VSIX.|
|[Riferimento allo schema di estensione VSIX 2,0](../extensibility/vsix-extension-schema-2-0-reference.md)|Un manifesto VSIX descrive il contenuto di un file di distribuzione con *estensione VSIX* . Il file di distribuzione consente di installare un'estensione di Visual Studio tramite la finestra di dialogo **estensioni e aggiornamenti** .|
|[Individuare e usare le estensioni di Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)|Viene illustrato come utilizzare la finestra di dialogo **estensioni e aggiornamenti** per installare, rimuovere, attivare e disattivare le estensioni.|

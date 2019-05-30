---
title: Localizzazione di pacchetti VSIX | Microsoft Docs
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e0ef2cc0c2404a2148f471d12f313b158f3bd64
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344566"
---
# <a name="localizing-vsix-packages"></a>Localizzazione di pacchetti VSIX

È possibile localizzare un pacchetto VSIX tramite la creazione di un' *vsixlangpack* file per ogni lingua di destinazione e inserendo i file nella cartella corretta. Quando viene installato un pacchetto di aggiornamento, viene visualizzato il nome localizzato dell'estensione con una descrizione localizzata. Se si specifica un file di licenza localizzata o un URL che punta alle informazioni localizzate, vengono anche visualizzate.

Se il contenuto del pacchetto VSIX include un pacchetto VSPackage che aggiunge i comandi di menu o altra interfaccia utente, vedere [localizzare i comandi di menu](../extensibility/localizing-menu-commands.md) per informazioni sulla localizzazione dei nuovi elementi dell'interfaccia utente.

## <a name="directory-structure"></a>Struttura di directory

 Quando un utente installa un'estensione **estensioni e aggiornamenti** controlla il livello principale del pacchetto VSIX per una cartella il cui nome corrisponde le impostazioni locali di Visual Studio del computer di destinazione. Se **estensioni e aggiornamenti** trova un *con estensione vsixlangpack* file nella cartella, lo sostituisce con i valori localizzati in tale file per i valori corrispondenti nel *vsixmanifest*file. Questi valori vengono visualizzati quando viene installato l'estensione. Nell'esempio seguente mostra la struttura di directory per un pacchetto VSIX che viene localizzato in spagnolo (es-ES) e francese (fr-FR).

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
> I modelli di progetto VSIX supportata la [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] generare un manifesto VSIX e assegnargli il nome *vsixmanifest*. Quando Visual Studio compila il progetto, verrà copiato il contenuto del file in Extension. vsixmanifest nel pacchetto VSIX.

## <a name="the-extensionvsixlangpack-file"></a>Il file vsixlangpack

Il *vsixlangpack* file segue la [dello schema di Language Pack VSIX 2.0](../extensibility/vsix-language-pack-schema-2-0-reference.md). Questo schema ha un `PackageLanguagePackManifest`, cui è seguita immediatamente da un `Metadata` elemento figlio. L'elemento dei metadati può contenere fino a 6 elementi figlio `DisplayName`, `Description`, `MoreInfo`, `License`, `ReleaseNotes`, e `Icon`. Tali elementi figlio corrispondano per il `DisplayName`, `Description`, `MoreInfo`, `License`, `ReleaseNotes`, e `Icon` gli elementi figlio del `Metadata` elemento del *Extension. vsixmanifest*file.

Quando si crea un file vsixlangpack, è necessario impostare il `Include in Vsix` proprietà `true`. In caso contrario, il testo di installazione localizzata verrà ignorato.

### <a name="to-set-the-include-in-vsix-property"></a>Per impostare l'inclusione in proprietà Vsix

1. Nelle **Esplora soluzioni**, fare doppio clic su file vsixlangpack e quindi fare clic su **proprietà**.

2. Nel **griglia delle proprietà**, fare clic su **Includi in Vsix**e impostarne il valore su `true`.

## <a name="example"></a>Esempio

### <a name="description"></a>Descrizione

L'esempio seguente illustra le parti pertinenti di un *Extension. vsixmanifest* file. Il file include anche il corrispondente *vsixlangpack* file per lo spagnolo. I valori dal language pack di sostituiscono i valori dal manifesto se le impostazioni locali di Visual Studio del computer di destinazione sono impostata sullo spagnolo.

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

## <a name="see-also"></a>Vedere anche

|Titolo|Descrizione|
|-----------|-----------------|
|[Riferimenti allo schema 2.0 dei Language Pack VSIX](/visualstudio/extensibility/vsix-language-pack-schema-2-0-reference)|Un language pack VSIX descrive le informazioni di localizzazione di un file di distribuzione VSIX.|
|[Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Descrive la struttura e contenuto di un pacchetto vsix.|
|[Localizzare i comandi di menu](../extensibility/localizing-menu-commands.md)|Mostra come localizzare altre risorse di testo in un'estensione.|
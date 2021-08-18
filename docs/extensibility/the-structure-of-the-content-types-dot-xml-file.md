---
title: Struttura dell'oggetto [Content_types].xml File | Microsoft Docs
description: Informazioni sulla struttura del file dei tipi di contenuto, che contiene informazioni sui tipi di contenuto in un pacchetto VSIX.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 681b2877983762ec0601543ae996748612fd3812
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049311"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>Struttura del file [Content_types].xml
Contiene informazioni sui tipi di contenuto in un pacchetto VSIX. Visual Studio usa il file [Content_Types].xml per installare il pacchetto, ma non installa il file stesso.

> [!NOTE]
> Anche se questo argomento si applica solo ai file [Content_Type].xml usati nei pacchetti VSIX, il tipo di file [Content_Types].xml fa parte dello standard *Open Packaging Conventions (OPC).* Per altre informazioni, vedere [OPC: A New Standard for Packaging Your Data](/archive/msdn-magazine/2007/august/opc-a-new-standard-for-packaging-your-data) nel sito Web MSDN.

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Le sezioni seguenti descrivono l'elemento radice, i relativi attributi e gli elementi figlio.

### <a name="root-element"></a>Elemento radice

|Elemento|Descrizione|
|-------------|-----------------|
|`Types`|Contiene elementi figlio che enumerano i tipi di file nel pacchetto VSIX.|

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|`Xmlns`|(Obbligatorio). Percorso dello schema usato per questo file [Content_Types].xml.|

### <a name="attribute-name-attribute"></a>{Nome attributo} Attributo

| Valore | Descrizione |
| - | - |
| `http://schemas.openformats.org/package/2006/content-types` | Percorso dello schema dei tipi di contenuto. |

### <a name="child-elements"></a>Elementi figlio
 L'elemento `Types` può contenere un numero illimitato di elementi `Default`.

|Elemento|Descrizione|
|-------------|-----------------|
|`Default`|Descrive un tipo di contenuto nel pacchetto VSIX. Ogni tipo di file nel pacchetto deve avere un proprio `Default` elemento.|

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|`Extension`|Estensione di file di un file nel pacchetto VSIX.|
|`ContentType`|Descrive il tipo di contenuto associato all'estensione di file.|

### <a name="attribute-name-attribute"></a>{Nome attributo} Attributo
 Visual Studio riconosce i valori `ContentType` seguenti per i tipi `Extension` associati.

|Estensione|ContentType|
|---------------|-----------------|
|txt|text/plain|
|pkgdef|text/plain|
|Xml|text/xml|
|vsixmanifest|text/xml|
|htm o html|text/html|
|Rtf|application/rtf|
|pdf|application/pdf|
|GIF|image/gif|
|jpg o jpeg|image/jpg|
|tiff|image/tiff|
|vsix|application/zip|
|zip|application/zip|
|Libreria dll|application/octet-stream|
|tutti gli altri tipi di file|application/octet-stream|

## <a name="example"></a>Esempio

### <a name="description"></a>Descrizione
 Il file [Content_Types].xml seguente descrive un tipico pacchetto VSIX.

### <a name="code"></a>Codice

```
<?xml version="1.0" encoding="utf-8" ?>
<Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">
    <Default Extension="vsixmanifest" ContentType="text/xml" />
    <Default Extension="dll" ContentType="application/octet-stream" />
    <Default Extension="png" ContentType="application/octet-stream" />
    <Default Extension="txt" ContentType="text/plain" />
    <Default Extension="pkgdef" ContentType="text/plain" />
</Types>
```

## <a name="see-also"></a>Vedi anche
- [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Informazioni di riferimento sullo schema dell'estensione VSIX 1.0](/previous-versions/dd393700(v=vs.110))
- [OPC: un nuovo standard per la creazione di pacchetti dei dati](/archive/msdn-magazine/2007/august/opc-a-new-standard-for-packaging-your-data)
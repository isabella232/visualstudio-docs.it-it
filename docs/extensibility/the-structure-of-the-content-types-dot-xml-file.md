---
title: Struttura del file [Content_types]. XML | Microsoft Docs
description: Informazioni sulla struttura del file dei tipi di contenuto, che contiene informazioni sui tipi di contenuto in un pacchetto VSIX.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 38348661946be3894332d49177f972410563b716
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895207"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>Struttura del file [Content_types].xml
Contiene informazioni sui tipi di contenuto in un pacchetto VSIX. Visual Studio usa il file [Content_Types]. XML per installare il pacchetto, ma non installa il file stesso.

> [!NOTE]
> Sebbene questo argomento si riferisca solo ai file [Content_Type]. XML usati nei pacchetti VSIX, il tipo di file [Content_Types]. XML fa parte dello standard *OPC (Open Packaging Conventions)* . Per ulteriori informazioni, vedere [OPC: nuovo standard per la creazione di pacchetti di dati](/archive/msdn-magazine/2007/august/opc-a-new-standard-for-packaging-your-data) nel sito Web MSDN.

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti l'elemento radice e i relativi attributi ed elementi figlio.

### <a name="root-element"></a>Elemento radice

|Elemento|Descrizione|
|-------------|-----------------|
|`Types`|Contiene gli elementi figlio che enumerano i tipi di file nel pacchetto VSIX.|

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|`Xmlns`|(Obbligatorio). Percorso dello schema utilizzato per il file [Content_Types]. XML.|

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
|`Extension`|Estensione del nome file di un file nel pacchetto VSIX.|
|`ContentType`|Descrive il tipo di contenuto associato all'estensione del nome file.|

### <a name="attribute-name-attribute"></a>{Nome attributo} Attributo
 Visual Studio riconosce i `ContentType` valori seguenti per i `Extension` tipi associati.

|Estensione|ContentType|
|---------------|-----------------|
|txt|text/plain|
|pkgdef|text/plain|
|Xml|text/xml|
|vsixmanifest|text/xml|
|htm o HTML|text/html|
|RTF|applicazione/RTF|
|pdf|applicazione/PDF|
|GIF|image/gif|
|jpg o JPEG|immagine/jpg|
|tiff|image/tiff|
|vsix|applicazione/zip|
|zip|applicazione/zip|
|Libreria dll|application/octet-stream|
|tutti gli altri tipi di file|application/octet-stream|

## <a name="example"></a>Esempio

### <a name="description"></a>Descrizione
 Il seguente file [Content_Types]. XML descrive un tipico pacchetto VSIX.

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
- [Riferimento allo schema di estensione VSIX 1,0](/previous-versions/dd393700(v=vs.110))
- [OPC: nuovo standard per il packaging dei dati](/archive/msdn-magazine/2007/august/opc-a-new-standard-for-packaging-your-data)
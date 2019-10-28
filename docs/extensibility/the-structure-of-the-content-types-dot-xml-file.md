---
title: Struttura del file [Content_Types]. XML | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aac250053f90d99e7db27a9862d2dc1b33fadbfb
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72983033"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>Struttura del file [Content_types].xml
Contiene informazioni sui tipi di contenuto in un pacchetto VSIX. Visual Studio usa il file [Content_Types]. XML per installare il pacchetto, ma non installa il file stesso.

> [!NOTE]
> Sebbene questo argomento sia valido solo per i file [Content_Type]. XML usati nei pacchetti VSIX, il tipo di file [Content_Types]. XML fa parte dello standard *OPC (Open Packaging Conventions)* . Per ulteriori informazioni, vedere [OPC: nuovo standard per la creazione di pacchetti di dati](https://msdn.microsoft.com/magazine/cc163372.aspx) nel sito Web MSDN.

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

| Value | Descrizione |
| - | - |
| http://schemas.openformats.org/package/2006/content-types | Percorso dello schema dei tipi di contenuto. |

### <a name="child-elements"></a>Elementi figlio
 L'elemento `Types` può contenere un numero qualsiasi di elementi di `Default`.

|Elemento|Descrizione|
|-------------|-----------------|
|`Default`|Descrive un tipo di contenuto nel pacchetto VSIX. Ogni tipo di file nel pacchetto deve avere un proprio elemento `Default`.|

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|`Extension`|Estensione del nome file di un file nel pacchetto VSIX.|
|`ContentType`|Descrive il tipo di contenuto associato all'estensione del nome file.|

### <a name="attribute-name-attribute"></a>{Nome attributo} Attributo
 Visual Studio riconosce i valori `ContentType` seguenti per i tipi di `Extension` associati.

|Estensione|contentType|
|---------------|-----------------|
|txt|testo/normale|
|pkgdef|testo/normale|
|xml|text/xml|
|vsixmanifest|text/xml|
|htm o HTML|testo/HTML|
|RTF|applicazione/RTF|
|PDF|applicazione/PDF|
|gif|immagine/gif|
|jpg o JPEG|immagine/jpg|
|TIFF|immagine/TIFF|
|vsix|applicazione/zip|
|zip|applicazione/zip|
|dll|application/octet-stream|
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

## <a name="see-also"></a>Vedere anche
- [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Riferimento allo schema di estensione VSIX 1,0](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
- [OPC: nuovo standard per il packaging dei dati](https://msdn.microsoft.com/magazine/cc163372.aspx)
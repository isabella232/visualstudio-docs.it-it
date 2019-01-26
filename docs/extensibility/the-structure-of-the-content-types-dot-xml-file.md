---
title: La struttura del File [Content_types] XML | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 80013faf174900c4e94bf452f6f19c0ac9bfbeba
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54956493"
---
# <a name="the-structure-of-the-contenttypesxml-file"></a>Struttura del file [Content_types].xml
Contiene informazioni sui tipi di contenuto in un pacchetto VSIX. Visual Studio Usa il file [Content_Types] XML per installare il pacchetto, ma non installa il file stesso.  
  
> [!NOTE]
>  Sebbene in questo argomento si applica solo a [Content_Types]. XML file che vengono usati nei pacchetti VSIX, il tipo di file [Content_Types] XML fa parte di *Open Packaging Conventions (OPC)* standard. Per altre informazioni, vedere [OPC: Un nuovo Standard per la creazione di pacchetti dati](http://go.microsoft.com/fwlink/?LinkID=148207) sul sito Web MSDN.  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Le sezioni seguenti descrivono l'elemento radice e i relativi attributi ed elementi figlio.  
  
### <a name="root-element"></a>Elemento radice  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|`Types`|Contiene gli elementi figlio che enumera i tipi di file nel pacchetto VSIX.|  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Xmlns`|Obbligatorio. Il percorso dello schema utilizzato per questo file [Content_Types] XML.|  
  
### <a name="attribute-name-attribute"></a>{Nome dell'attributo} Attributo  
  
| Value | Descrizione |
| - | - |
| http://schemas.openformats.org/package/2006/content-types | Il percorso dello schema di tipi di contenuto. |
  
### <a name="child-elements"></a>Elementi figlio  
 Il `Types` elemento può contenere un numero qualsiasi di `Default` elementi.  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|`Default`|Descrive un tipo di contenuto nel pacchetto VSIX. Ogni tipo di file del pacchetto deve avere un proprio `Default` elemento.|  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Extension`|L'estensione di un file nel pacchetto VSIX.|  
|`ContentType`|Descrive il tipo di contenuto che è associato con l'estensione del nome file.|  
  
### <a name="attribute-name-attribute"></a>{Nome dell'attributo} Attributo  
 Visual Studio riconosce seguenti `ContentType` i valori per la proprietà associata `Extension` tipi.  
  
|Estensione|ContentType|  
|---------------|-----------------|  
|txt|text/plain|  
|pkgdef|text/plain|  
|xml|text/xml|  
|vsixmanifest|text/xml|  
|htm o html|testo/html|  
|rtf|applicazione/rtf|  
|pdf|Application/pdf|  
|gif|image/gif|  
|jpg o jpeg|image/jpg|  
|tiff|image/tiff|  
|vsix|Application/zip|  
|zip|Application/zip|  
|dll|application/octet-stream|  
|tutti gli altri tipi di file|application/octet-stream|  
  
## <a name="example"></a>Esempio  
  
### <a name="description"></a>Descrizione  
 Il file [Content_Types] XML seguente viene descritto un pacchetto VSIX tipico.  
  
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
 [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Riferimenti su VSIX Extension Schema 1.0](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC: Un nuovo Standard per l'assemblaggio dei dati](http://go.microsoft.com/fwlink/?LinkID=148207)
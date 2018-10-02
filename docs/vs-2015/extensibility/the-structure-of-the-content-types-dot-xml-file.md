---
title: La struttura del Content_types]. XML File | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 89c5e1bab9f8cbe8cd6e2b980013c6bfdf4bc039
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540464"
---
# <a name="the-structure-of-the-contenttypesxml-file"></a>La struttura del Content_types]. XML File
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [struttura del File [Content_types] XML](https://docs.microsoft.com/visualstudio/extensibility/the-structure-of-the-content-types-dot-xml-file).  
  
Contiene informazioni sui tipi di contenuto in un pacchetto VSIX. Visual Studio Usa il file [Content_Types] XML per installare il pacchetto, ma non installa il file stesso.  
  
> [!NOTE]
>  Sebbene in questo argomento si applica solo a [Content_Types]. XML file che vengono usati nei pacchetti VSIX, il tipo di file [Content_Types] XML fa parte di *Open Packaging Conventions (OPC)* standard. Per altre informazioni, vedere [OPC: un nuovo Standard per la creazione di pacchetti di dati](http://go.microsoft.com/fwlink/?LinkID=148207) sul sito Web MSDN.  
  
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
  
|Valore|Descrizione|  
|-----------|-----------------|  
|http://schemas.openformats.org/package/2006/content-types|Il percorso dello schema di tipi di contenuto.|  
  
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
|formato RTF|applicazione/rtf|  
|PDF|Application/pdf|  
|GIF|image/gif|  
|jpg o jpeg|immagine/jpg|  
|TIFF|immagine/tiff|  
|vsix|Application/zip|  
|file ZIP|Application/zip|  
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
 [Riferimenti su VSIX Extension Schema 1.0](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC: Un nuovo Standard per l'assemblaggio dei dati](http://go.microsoft.com/fwlink/?LinkID=148207)


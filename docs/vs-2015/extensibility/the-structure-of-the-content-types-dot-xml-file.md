---
title: Il file Structure of the Content_types].xml Documenti Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2d6eca44c08cf35e7b2075965c1b6139e7fb95bc
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395362"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>Struttura del file [Content_types].xml
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Contiene informazioni sui tipi di contenuto in un pacchetto VSIX. Visual Studio utilizza il file [Content_Types].xml per installare il pacchetto, ma non installa il file stesso.  
  
> [!NOTE]
> Anche se questo argomento si applica solo ai file [Content_Type].xml utilizzati nei pacchetti VSIX, il tipo di file [Content_Types].xml fa parte dello standard *Open Packaging Conventions (OPC).* Per ulteriori informazioni, vedere [OPC: A New Standard For Packaging Your Data](https://msdn.microsoft.com/magazine/cc163372.aspx) sul sito Web MSDN (informazioni in lingua inglese).  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti l'elemento radice e i relativi attributi ed elementi figlio.  
  
### <a name="root-element"></a>Elemento radice  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|`Types`|Contiene elementi figlio che enumerano i tipi di file nel pacchetto VSIX.|  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Xmlns`|(Obbligatorio.) Percorso dello schema utilizzato per questo file [Content_Types].xml.|  
  
### <a name="attribute-name-attribute"></a>"Nome dell'attributo" Attributo  
  
|                           valore                           |                Descrizione                |
|-----------------------------------------------------------|-------------------------------------------|
| `http://schemas.openformats.org/package/2006/content-types` | Percorso dello schema dei tipi di contenuto. |
  
### <a name="child-elements"></a>Elementi figlio  
 L'elemento `Types` può contenere un numero illimitato di elementi `Default`.  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|`Default`|Descrive un tipo di contenuto nel pacchetto VSIX. Ogni tipo di file nel `Default` pacchetto deve avere un proprio elemento.|  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Extension`|Estensione di un file nel pacchetto VSIX.|  
|`ContentType`|Descrive il tipo di contenuto associato all'estensione del nome file.|  
  
### <a name="attribute-name-attribute"></a>"Nome dell'attributo" Attributo  
 Visual Studio riconosce `ContentType` i valori `Extension` seguenti per i tipi associati.  
  
|Estensione|ContentType|  
|---------------|-----------------|  
|txt|text/plain|  
|pkgdef|text/plain|  
|Xml|text/xml|  
|vsixmanifest|text/xml|  
|htm o html|text/html|  
|Rtf|applicazione/rtf|  
|pdf|applicazione/pdf|  
|GIF|image/gif|  
|jpg o jpeg|immagine/jpg|  
|tiff|image/tiff|  
|vsix|applicazione/zip|  
|zip|applicazione/zip|  
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
  
## <a name="see-also"></a>Vedere anche  
 [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [VSIX Extension Schema 1.0 Reference](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC: un nuovo standard per l'imballaggio dei dati](https://msdn.microsoft.com/magazine/cc163372.aspx)

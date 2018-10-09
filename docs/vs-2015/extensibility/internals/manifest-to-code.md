---
title: Manifesttocode | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17ecacea-397d-4a97-b003-01bd5d56e936
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f0809d44afb6777f26ea6b863ede765d93b5d24f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517877"
---
# <a name="manifest-to-code"></a>Manifest to Code
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [manifesto al codice](https://docs.microsoft.com/visualstudio/extensibility/internals/manifest-to-code).  
  
Il manifesto per lo strumento di codice è un'applicazione console che accetta un file .imagemanifest per il servizio di immagini di Visual Studio e genera un wrapper o i file per fare riferimento ai valori del manifesto di immagini in C++, c#, VB o file con estensione vsct per le estensioni di Visual Studio. Questo strumento genera i file di wrapper che possono essere utilizzati per le immagini richiedente da Visual Studio Image Service direttamente o per passare i valori del manifesto tramite le API, se il codice non gestisce la propria interfaccia utente e per il rendering.  
  
## <a name="how-to-use-the-tool"></a>Come usare lo strumento  
 **Sintassi**  
  
 ManifestToCode /manifest:\<file di immagine manifesto > /language:\<linguaggio del codice > \<Args facoltativo >  
  
 **Argomenti**  
  
||||  
|-|-|-|  
|**Nome del commutatore**|**Note**|**Obbligatoria o facoltativa**|  
|/manifest|Il percorso del manifesto dell'immagine da utilizzare per creare o aggiornare il wrapper di codice.|Obbligatorio|  
|/Language|La lingua in cui generare il wrapper di codice.<br /><br /> I valori validi: CPP, C++, CS, CSharp, c#, VB o VSCT i valori sono tra maiuscole e minuscole.<br /><br /> Per il linguaggio VSCT opzione, /monikerClass, /classAccess e /namespace opzioni vengono ignorate.|Obbligatorio|  
|/imageIdClass|Il nome del imageIdClass e il file associato creato dallo strumento. Per l'opzione di linguaggio C++, vengono generati solo i file con estensione h.<br /><br /> Valore predefinito: \<percorso del manifesto > \MyImageIds.\< Lang Ext >|Facoltativo|  
|/monikerClass|Il nome del monikerClass e il file associato creato dallo strumento. Per l'opzione di linguaggio C++, vengono generati solo i file con estensione h. Questo viene ignorato per il linguaggio VSCT.<br /><br /> Valore predefinito: \<percorso del manifesto > \MyMonikers.\< Lang Ext >|Facoltativo|  
|/classAccess|Il modificatore di accesso per il imageIdClass e il monikerClass. Assicurarsi che il modificatore di accesso è valido per il linguaggio specificato. Questo viene ignorato per l'opzione di linguaggio VSCT.<br /><br /> Predefinito: pubblico|Facoltativo|  
|/Namespace|Lo spazio dei nomi definito all'interno del wrapper di codice. Questo viene ignorato per l'opzione di linguaggio VSCT. Entrambi '.' o ':: ' sono separatori di spazio dei nomi valido, indipendentemente dall'opzione di linguaggio scelto.<br /><br /> Predefinito: MyImages|Facoltativo|  
|/noLogo|Impostazione di questo flag arresta prodotto e informazioni sul copyright di stampare le informazioni.|Facoltativo|  
|/?|Stampare le informazioni della Guida.|Facoltativo|  
|/help|Stampare le informazioni della Guida.|Facoltativo|  
  
 **Esempi**  
  
-   ManifestToCode /manifest:D:\MyManifest.imagemanifest c:\Northwind.cs  
  
-   ManifestToCode /manifest:D:\MyManifest.imagemanifest /language:C++ /namespace: My:: Namespace /imageIdClass:MyImageIds /monikerClass:MyMonikers /classAccess:friend  
  
-   ManifestToCode /manifest:D:\MyManifest.imagemanifest /language:VSCT /imageIdClass:MyImageIds  
  
## <a name="notes"></a>Note  
  
-   È consigliabile utilizzare questo strumento con manifesti di immagine che sono stati generati dal manifesto dallo strumento di risorse.  
  
-   Lo strumento analizza solo le voci di simboli per generare il wrapper del codice. Se un manifesto di immagini non contiene simboli, i wrapper del codice generato sarà vuoti. Se è presente un'immagine o un set di immagini nel manifesto dell'immagine che non utilizzano i simboli, essi verranno esclusi dal wrapper codice.  
  
## <a name="sample-output"></a>Esempio di output  
 **Wrapper c#**  
  
 Le classi di una coppia di ID immagine semplice e il moniker di immagini per c# sarà simile al codice riportato di seguito:  
  
```csharp  
//-----------------------------------------------------------------------------  
// <auto-generated>  
//     This code was generated by the ManifestToCode tool.  
//     Tool Version: 14.0.15198  
// </auto-generated>  
//-----------------------------------------------------------------------------  
  
using System;  
  
namespace MyImages  
{  
    public static class MyImageIds  
    {  
        public static readonly Guid AssetsGuid = new Guid("{442d8739-efde-46a4-8f29-e3a1e5e7f8b4}");  
  
        public const int MyImage1 = 0;  
        public const int MyImage2 = 1;  
    }  
}  
//-----------------------------------------------------------------------------  
// <auto-generated>  
//     This code was generated by the ManifestToCode tool.  
//     Tool Version: 14.0.15198  
// </auto-generated>  
//-----------------------------------------------------------------------------  
  
using Microsoft.VisualStudio.Imaging.Interop;  
  
namespace MyImages  
{  
    public static class MyMonikers  
    {  
        public static ImageMoniker MyImage1 { get { return new ImageMoniker { Guid = MyImageIds.AssetsGuid, Id = MyImageIds.MyImage1 }; } }  
        public static ImageMoniker MyImage2 { get { return new ImageMoniker { Guid = MyImageIds.AssetsGuid, Id = MyImageIds.MyImage2 }; } }  
    }  
}  
```  
  
 **Wrapper C++**  
  
 Le classi di una coppia di ID immagine semplice e il moniker di immagini per C++ sarà simile al codice riportato di seguito:  
  
```cpp  
//-----------------------------------------------------------------------------  
// <auto-generated>  
//     This code was generated by the ManifestToCode tool.  
//     Tool Version: 14.0.15198  
// </auto-generated>  
//-----------------------------------------------------------------------------  
  
#pragma once  
  
#include <guiddef.h>  
  
namespace MyImages {  
  
class MyImageIds {  
public:  
  
    static const GUID AssetsGuid;  
  
    static const int MyImage1 = 0;  
    static const int MyImage2 = 1;  
  
};  
  
__declspec(selectany) const GUID MyImageIds::AssetsGuid = {0x442d8739,0xefde,0x46a4,{0x8f,0x29,0xe3,0xa1,0xe5,0xe7,0xf8,0xb4}};  
  
}  
//-----------------------------------------------------------------------------  
// <auto-generated>  
//     This code was generated by the ManifestToCode tool.  
//     Tool Version: 14.0.15198  
// </auto-generated>  
//-----------------------------------------------------------------------------  
  
#pragma once  
  
#include "ImageParameters140.h"  
#include "MyImageIds.h"  
  
namespace MyImages {  
  
class MyMonikers {  
public:  
  
    static const ImageMoniker MyImage1;  
    static const ImageMoniker MyImage2;  
  
};  
  
__declspec(selectany) const ImageMoniker MyMonikers::MyImage1 = { MyImageIds::AssetsGuid, MyImageIds::MyImage1 };  
__declspec(selectany) const ImageMoniker MyMonikers::MyImage2 = { MyImageIds::AssetsGuid, MyImageIds::MyImage2 };  
  
}  
```  
  
 **Wrapper Visual Basic**  
  
 Le classi di una coppia di ID immagine semplice e il moniker di immagini per Visual Basic sarà simile al codice riportato di seguito:  
  
```vb  
' -----------------------------------------------------------------------------  
'  <auto-generated>  
'      This code was generated by the ManifestToCode tool.  
'      Tool Version: 14.0.15198  
'  </auto-generated>  
' -----------------------------------------------------------------------------  
  
Imports System  
  
Namespace MyImages  
  
    Public Module MyImageIds  
  
        Public Shared ReadOnly AssetsGuid As Guid = New Guid("{442d8739-efde-46a4-8f29-e3a1e5e7f8b4}")  
  
        Public Const MyImage1 As Integer = 0  
        Public Const MyImage2 As Integer = 1  
  
    End Module  
  
End Namespace  
' -----------------------------------------------------------------------------  
'  <auto-generated>  
'      This code was generated by the ManifestToCode tool.  
'      Tool Version: 14.0.15198  
'  </auto-generated>  
' -----------------------------------------------------------------------------  
  
Imports Microsoft.VisualStudio.Imaging.Interop  
  
Namespace MyImages  
  
    Public Module MyMonikers  
  
        Public Readonly Property MyImage1  
            Get  
                Return New ImageMoniker With {.Guid = MyImageIds.AssetsGuid, .Id = MyImageIds.MyImage1}  
            End Get  
        End Property  
  
        Public Readonly Property MyImage2  
            Get  
                Return New ImageMoniker With {.Guid = MyImageIds.AssetsGuid, .Id = MyImageIds.MyImage2}  
            End Get  
        End Property  
  
    End Module  
  
End Namespace  
```  
  
 **Wrapper VSCT**  
  
 Un set di ID di immagini per un file con estensione vsct sarà simile al seguente:  
  
```xml  
<?xml version='1.0' encoding='utf-8'?>  
<!--  
 [auto-generated]  
     This code was generated by the ManifestToCode tool.  
     Tool Version: 14.0.15198  
 [/auto-generated]  
-->  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">  
  <Symbols>  
    <GuidSymbol name="AssetsGuid" value="{442d8739-efde-46a4-8f29-e3a1e5e7f8b4}">  
      <IDSymbol name="MyImage1" value="0" />  
      <IDSymbol name="MyImage2" value="1" />  
    </GuidSymbol>  
  </Symbols>  
</CommandTable>  
```

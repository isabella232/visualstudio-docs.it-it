---
title: Elemento VisibilityConstraints | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- VisibilityConstraints
helpviewer_keywords:
- VSCT XML schema elements, VisibilityConstraints
- VisibilityConstraints element (VSCT XML schema)
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 06f6a74fabfc1bd86f54656c6b30b55690940a0d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62585126"
---
# <a name="visibilityconstraints-element"></a>Elemento VisibilityConstraints
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'elemento VisibilityConstraints determina la visibilità statica di gruppi di comandi e barre degli strumenti. La visibilità viene prima controllata dal [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Integrated Development Environment (IDE) senza caricare il pacchetto VSPackage.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<VisibilityConstraints>  
  <VisibilityConstraint>... </VisibilityConstraint>  
  <VisibilityConstraint>... </VisibilityConstraint>  
</VisibilityConstraint>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|Condizione|facoltativo. Vedere [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento VisibilityItem](../extensibility/visibilityitem-element.md)|Determina la visibilità statica dei comandi e delle barre degli strumenti.|  
|[VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Determina la visibilità statica di gruppi di comandi e barre degli strumenti.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano i comandi (ad esempio, le voci di menu, i menu, le barre degli strumenti e le caselle combinate) forniti da un VSPackage all'IDE.|  
  
## <a name="example"></a>Esempio  
  
```  
<VisibilityConstraints>  
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"  
    context="guidNotViewSourceMode"/>  
</VisibilityConstraints>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento VisibilityItem](../extensibility/visibilityitem-element.md)   
 [File Visual Studio Command Table (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

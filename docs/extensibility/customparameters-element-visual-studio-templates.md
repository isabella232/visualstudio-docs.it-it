---
title: Elemento CustomParameters (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameters
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: cf3efc91-1532-4022-bbb8-a18658424fee
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1f3816943ca3779b9110de2359fd10852330eb20
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54940258"
---
# <a name="customparameters-element-visual-studio-templates"></a>Elemento CustomParameters (modelli di Visual Studio)
Consente di raggruppare i parametri personalizzati che devono essere passati per la creazione guidata modello durante la procedura guidata effettua le sostituzioni di parametro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<CustomParameters>  
    <CustomParameter/>  
    <CustomParameter/>  
</CustomParameters>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
 Nessuno.  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|Elemento facoltativo.<br /><br /> Contiene un nome del parametro personalizzato e un valore da utilizzare quando viene creato un progetto o un elemento dal modello. Possono esistere zero o più elementi `CustomParameter` in un elemento `CustomParameters`.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Specifica il contenuto del modello.|  
  
## <a name="remarks"></a>Note  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come usare diversi parametri personalizzati in un modello. Quando viene creato un progetto o un elemento da un modello con i seguenti parametri personalizzati, tutte le istanze del `$color1$` e `$color2$` nel modello di file verranno sostituiti con `Red` e `Blue`, rispettivamente.  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento CustomParameter (modelli di Visual Studio)](../extensibility/customparameter-element-visual-studio-templates.md)   
 [Parametri del modello](../ide/template-parameters.md)   
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
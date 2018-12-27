---
title: Elemento CustomParameter (modelli di Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2efb89f53244f2a14031ef386021e83c48b5048c
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/18/2018
ms.locfileid: "53561278"
---
# <a name="customparameter-element-visual-studio-templates"></a>Elemento CustomParameter (modelli di Visual Studio)
Contiene un nome del parametro personalizzato e un valore da utilizzare quando viene creato un progetto o un elemento dal modello.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<CustomParameter Name="name" Value="value">  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Name`|Obbligatorio. Nome del parametro. Il formato per i parametri è $*nome*$.|  
|`Value`|Obbligatorio. Il valore di sostituzione per il parametro.|  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Consente di raggruppare i parametri personalizzati che devono essere passati per la creazione guidata modello durante la procedura guidata effettua le sostituzioni di parametro.|  
  
## <a name="remarks"></a>Note  
 Quando un modello contiene `CustomParameter` elementi, ogni istanza di `Name` attributo viene sostituito con il `Value` attributo nei file di progetto o un elemento creati.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come usare diversi parametri personalizzati in un modello. Quando viene creato un progetto o un elemento da un modello con i seguenti parametri personalizzati, tutte le istanze del `$color1$` e `$color2$` nel modello di file verranno sostituiti con `Red` e `Blue`, rispettivamente.  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento CustomParameters (modelli di Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md)   
 [Parametri del modello](../ide/template-parameters.md)   
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
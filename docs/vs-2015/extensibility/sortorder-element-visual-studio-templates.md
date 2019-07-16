---
title: Elemento SortOrder (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder
helpviewer_keywords:
- SortOrder element [Visual Studio Templates]
- <SortOrder> element [Visual Studio Templates]
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 825ec785a83cae0aaa8a31ae1375e956228b634e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68205520"
---
# <a name="sortorder-element-visual-studio-templates"></a>Elemento SortOrder (modelli di Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Specifica un valore che viene usato per disporre il modello, tra gli altri modelli della stessa categoria, così come appare in entrambi i **nuovo progetto** oppure **Aggiungi nuovo elemento** nella finestra di dialogo.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<SortOrder >  
  
## <a name="syntax"></a>Sintassi  
  
```  
<SortOrder> ... </SortOrder>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
 Nessuno.  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Classifica il modello in base alla categoria e definisce la modalità di visualizzazione nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento** .|  
  
## <a name="text-value"></a>Valore di testo  
 È necessario specificare un valore di testo.  
  
 Un `integer` che rappresenta il valore di ordinamento.  
  
## <a name="remarks"></a>Note  
 `SortOrder` è un elemento facoltativo. Il valore predefinito è 100 e tutti i valori devono essere multipli di 10.  
  
 Il `SortOrder` elemento viene ignorato per i modelli creati dall'utente. Tutti i modelli creati dall'utente vengono ordinati alfabeticamente.  
  
 I modelli che hanno valori di ordinamento insufficiente vengono visualizzati in uno il **nuovo progetto** o **Aggiungi nuovo elemento** finestra di dialogo prima dei modelli con valori di ordinamento elevata.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente vengono illustrati i metadati di un controllo standard [!INCLUDE[csprcs](../includes/csprcs-md.md)] modello di classe.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class template.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <SortOrder>290</SortOrder>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 In questo esempio, il `SortOrder` elemento è relativamente alto. È probabile che gli altri [!INCLUDE[csprcs](../includes/csprcs-md.md)] modelli di elemento avrà un `SortOrder` valore inferiore a `290` e verranno visualizzati prima di questo modello nel **nuovo elemento** nella finestra di dialogo.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)

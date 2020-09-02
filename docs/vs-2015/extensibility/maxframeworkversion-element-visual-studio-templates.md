---
title: Elemento MaxFrameworkVersion (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4a1c27e42574429dbb6b2eaeb140db484bf29db5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194321"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>Elemento MaxFrameworkVersion (modelli di Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Specifica la versione massima del .NET Framework richiesta dal modello. Determina se il modello viene visualizzato nella sezione **modelli** della finestra di dialogo **Aggiungi nuovo progetto** , in base al valore selezionato nella casella **versione Framework di destinazione** della finestra di dialogo **Aggiungi nuovo progetto** .  
  
 \<VSTemplate>  
 \<MaxFrameworkVersion>  
  
## <a name="syntax"></a>Sintassi  
  
```  
<MaxFrameworkVersion> ... </MaxFrameworkVersion>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Categorizza il modello e ne definisce la modalità di visualizzazione nella finestra di dialogo **nuovo progetto** o **Aggiungi nuovo elemento** .|  
  
## <a name="text-value"></a>Valore di testo  
 È necessario specificare un valore di testo.  
  
 Il testo deve essere il numero di versione più alto del .NET Framework consentito dal modello.  
  
## <a name="remarks"></a>Osservazioni  
 `MaxFrameworkVersion` è un elemento facoltativo. L'elemento nella `TemplateData` sezione del file con estensione vstemplate funge da filtro per la sezione **modelli** della finestra di dialogo **Aggiungi nuovo progetto** . Verranno visualizzati solo i modelli i cui requisiti .NET Framework sono inferiori ai `MaxFrameworkVersion` valori degli elementi, in base al valore selezionato nella casella **versione Framework di destinazione** della finestra di dialogo **Aggiungi nuovo progetto** . L' `MaxFrameworkVersion` elemento deve essere omesso a meno che non sia necessario, in modo da non causare inavvertitamente la visualizzazione dei modelli quando vengono usati con versioni più recenti del .NET Framework.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente vengono illustrati i metadati per un [!INCLUDE[csprcs](../includes/csprcs-md.md)] modello di classe standard.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class template.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <MaxFrameworkVersion>3.5</MaxFrameworkVersion>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 In questo esempio, la versione massima del .NET Framework richiesta dal modello, rappresentata da `MaxFrameworkVersion` , è 3,5. Il modello precedente verrà visualizzato solo quando si seleziona 3,0 o 3,5 nella casella **versione Framework di destinazione** della finestra di dialogo **Aggiungi nuovo progetto** .  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento allo schema di modello di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)

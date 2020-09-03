---
title: Elemento ProvideDefaultName (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName
helpviewer_keywords:
- ProvideDefaultName element [Visual Studio project templates]
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0bd18dd979436b02cc12a4dab5439bdb5f371e2d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193881"
---
# <a name="providedefaultname-element-visual-studio-templates"></a>Elemento ProvideDefaultName (modelli di Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Specifica se il [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sistema del progetto genererà un nome predefinito per il modello nella finestra di dialogo **Aggiungi nuovo elemento** o **nuovo progetto** .  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<ProvideDefaultName>  
  
## <a name="syntax"></a>Sintassi  
  
```  
<ProvideDefaultName> true/false </ProvideDefaultName>  
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
  
 Il testo deve essere `true` o `false` , che indica se generare o meno un nome predefinito per il modello nella finestra di **dialogo Aggiungi nuovo elemento** o **nuovo progetto** .  
  
## <a name="remarks"></a>Osservazioni  
 `ProvideDefaultName` è un elemento facoltativo. Il valore predefinito è `true`.  
  
 Se l' `ProvideDefaultName` elemento è `false` , le caselle **nome** della finestra di dialogo **Aggiungi nuovo elemento** e **nuovo progetto** contengono il valore `<Enter_name>` .  
  
 Usare l'elemento [defaultName](../extensibility/defaultname-element-visual-studio-templates.md) per specificare il nome predefinito del progetto o dell'elemento nelle finestre di dialogo **Aggiungi nuovo elemento** e **nuovo progetto** .  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente l' `ProvideDefaultName` elemento viene impostato su `false` .  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <ProvideDefaultName>false</ProvideDefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento allo schema di modello di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)

---
title: Fa riferimento all'elemento (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#References
helpviewer_keywords:
- <References> element [Visual Studio Templates]
- References element [Visual Studio Templates]
ms.assetid: 1969146d-46bf-422d-8d46-0e9493925003
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 454f8a0da24d331456eb3c638512257868a19c69
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54949012"
---
# <a name="references-element-visual-studio-templates"></a>Elemento References (modelli di Visual Studio)
Raggruppa i riferimenti all'assembly che il modello aggiunge ai progetti.  
  
 \<VSTemplate>  
 \<TemplateContent>  
 \<Riferimenti a >  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<References>  
    <Reference>... </Reference>  
    <Reference>... </Reference>  
    ...  
</References>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
 Nessuno.  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Riferimento](../extensibility/reference-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Specifica il riferimento all'assembly da aggiungere quando l'elemento viene aggiunto a un progetto. Deve esistere uno o più `Reference` elementi in un `References` elemento.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Specifica il contenuto del modello.|  
  
## <a name="remarks"></a>Note  
 `References` è un elemento figlio facoltativo di `TemplateContent`.  
  
 Il `Reference` e `References` elementi possono essere utilizzati solo nel *vstemplate* contenenti un `Type` valore dell'attributo `Item`.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato il `TemplateContent` elemento di un modello di elemento. Questo codice XML aggiunge i riferimenti per il *System. dll* e *System* assembly.  
  
```xml  
<TemplateContent>  
    <References>  
        <Reference>  
            <Assembly>  
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
        <Reference>  
            <Assembly>  
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
    </References>  
    ...  
</TemplateContent>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti dello schema di modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)

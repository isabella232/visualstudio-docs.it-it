---
title: Elemento Reference (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Reference
helpviewer_keywords:
- Reference element [Visual Studio templates]
- <Reference> element [Visual Studio templates]
ms.assetid: 852772ea-c324-42e9-8c8a-6d565414a109
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c3d67fd19122e160159a6f636516dbca582fe31d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193839"
---
# <a name="reference-element-visual-studio-templates"></a>Elemento Reference (modelli di Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Specifica il riferimento all'assembly da aggiungere quando l'elemento viene aggiunto a un progetto.  
  
 \<VSTemplate>  
 \<TemplateContent>  
 \<References>  
 \<Reference>  
  
## <a name="syntax"></a>Sintassi  
  
```  
<Reference>  
    <Assembly> ... </Assembly>  
</Reference>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
 Nessuno.  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Assembly](../extensibility/assembly-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Specifica le informazioni su un assembly utilizzato dal modello per aggiungere un riferimento a tale assembly ai progetti. Deve essere presente un `Assembly` elemento in ogni `Reference` elemento.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Riferimenti](../extensibility/references-element-visual-studio-templates.md)|Raggruppa i riferimenti agli assembly aggiunti dal modello ai progetti.|  
  
## <a name="remarks"></a>Osservazioni  
 `Reference` è un elemento figlio obbligatorio di `References`.  
  
 Gli `Reference` `References` elementi e possono essere utilizzati solo nei file con estensione vstemplate il cui `Type` valore di attributo è `Item` .  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l' `TemplateContent` elemento di un modello di elemento. Il codice XML aggiunge riferimenti agli assembly System.dll e System.Data.dll.  
  
```  
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
 [Riferimento allo schema di modello di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)

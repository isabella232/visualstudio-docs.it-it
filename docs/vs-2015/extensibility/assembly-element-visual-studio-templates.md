---
title: Elemento assembly (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio templates]
- <Assembly> element [Visual Studio templates]
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 10c894f3507ae760624b6ae18f785aae6016cd5e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184701"
---
# <a name="assembly-element-visual-studio-templates"></a>Elemento Assembly (modelli di Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Specifica le informazioni su un assembly utilizzato dal modello per aggiungere un riferimento a tale assembly ai progetti.  
  
 \<VSTemplate>  
 \<TemplateContent>  
 \<References>  
 \<Reference>  
 \<Assembly>  
  
## <a name="syntax"></a>Sintassi  
  
```  
<Assembly> AssemblyName </Assembly>  
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
|[Riferimento](../extensibility/reference-element-visual-studio-templates.md)|Specifica il riferimento all'assembly da aggiungere quando l'elemento viene aggiunto a un progetto.|  
  
## <a name="text-value"></a>Valore di testo  
 È necessario specificare un valore di testo.  
  
 Questo testo specifica l'assembly da aggiungere a un progetto quando viene creata un'istanza del modello di elemento. Il nome dell'assembly deve essere specificato in uno dei modi seguenti:  
  
- Come nome completo dell'assembly. Ad esempio:  
  
    ```  
    <Assembly>  
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.  
    </Assembly>  
    ```  
  
- Come riferimento di testo semplice. Ad esempio:  
  
    ```  
    <Assembly> System </Assembly>  
    ```  
  
## <a name="remarks"></a>Osservazioni  
 `Assembly` è un elemento figlio obbligatorio di `Reference`.  
  
 Gli `Reference` `References,` elementi, e `Assembly` possono essere utilizzati solo nei file con estensione vstemplate il cui `Type` valore di attributo è `Item` .  
  
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

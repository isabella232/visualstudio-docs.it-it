---
title: 'Procedura: impostare gli attributi CLR in un elemento | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
ms.assetid: b3db3c74-920c-4701-9544-6f75cbe8b7c9
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: b77e0f1f31c0f617e80a27de4e1d0ab1d0b3d2eb
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49264022"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Procedura: impostare gli attributi CLR in un elemento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gli attributi personalizzati sono speciali attributi che possono essere aggiunti a diagrammi, forme, connettori e gli elementi del dominio. È possibile aggiungere qualsiasi attributo che eredita dal `System.Attribute` classe.  
  
### <a name="to-add-a-custom-attribute"></a>Per aggiungere un attributo personalizzato  
  
1.  Nel **DSL Explorer**, selezionare l'elemento a cui si desidera aggiungere un attributo personalizzato.  
  
2.  Nel **delle proprietà** finestra, accanto al **Custom Attributes** proprietà, fare clic su Sfoglia (**...** ) icona.  
  
     Il **Modifica attributi** verrà visualizzata la finestra di dialogo.  
  
3.  Nel **Name** colonna, fare clic su  **\<Aggiungi attributo >** e digitare il nome dell'attributo. Premere INVIO.  
  
4.  La riga sotto il nome dell'attributo Mostra le parentesi. In questa riga digitare un tipo di parametro per l'attributo (ad esempio, `string`), quindi premere INVIO.  
  
5.  Nel **proprietà Name** colonna, digitare un nome appropriato, ad esempio, `MyString`.  
  
6.  Fare clic su **OK**.  
  
     Il **Custom Attributes** proprietà Visualizza ora l'attributo nel formato seguente:  
  
     `[` *AttributeName* `(` *ParameterName* `=` *tipo* `)]`  
  
## <a name="see-also"></a>Vedere anche  
 [Glossario sugli strumenti Domain-Specific Language](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)




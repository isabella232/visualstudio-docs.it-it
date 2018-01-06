---
title: 'Procedura: impostare gli attributi CLR in un elemento | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.dsltools.EditAttributesDialog
helpviewer_keywords: Domain-Specific Language, custom attrributes
ms.assetid: b3db3c74-920c-4701-9544-6f75cbe8b7c9
caps.latest.revision: "19"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: d18a19debb8208c53d23bc5c187e0044a1303f08
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Procedura: impostare gli attributi CLR in un elemento
Gli attributi personalizzati sono attributi speciali che è possibile aggiungere diagrammi, forme, i connettori e gli elementi del dominio. È possibile aggiungere qualsiasi attributo che eredita la `System.Attribute` classe.  
  
### <a name="to-add-a-custom-attribute"></a>Per aggiungere un attributo personalizzato  
  
1.  Nel **Esplora DSL**, selezionare l'elemento a cui si desidera aggiungere un attributo personalizzato.  
  
2.  Nel **proprietà** finestra, accanto al **attributi personalizzati** proprietà, fare clic su Sfoglia (**...** ) icona.  
  
     Il **Modifica attributi** verrà visualizzata la finestra di dialogo.  
  
3.  Nel **nome** colonna, fare clic su  **\<aggiungere attributo >** e digitare il nome dell'attributo. Premere INVIO.  
  
4.  La riga sotto il nome di attributo Mostra le parentesi. In questa riga di un tipo di parametro per l'attributo di tipo (ad esempio, `string`), quindi premere INVIO.  
  
5.  Nel **nome proprietà** colonna, digitare un nome appropriato, ad esempio, `MyString`.  
  
6.  Fare clic su **OK**.  
  
     Il **attributi personalizzati** proprietà Visualizza ora l'attributo nel formato seguente:  
  
     `[`*AttributeName* `(` *ParameterName* `=` *tipo*`)]`  
  
## <a name="see-also"></a>Vedere anche  
 [Glossario di strumenti di linguaggio specifico di dominio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)
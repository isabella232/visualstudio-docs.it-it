---
title: 'Procedura: impostare gli attributi CLR in un elemento | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 919f77955426ada0b772b1eb1f4c0adfffb59b81
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
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
  
     `[` *AttributeName* `(` *ParameterName* `=` *tipo* `)]`  
  
## <a name="see-also"></a>Vedere anche  
 [Glossario di strumenti di linguaggio specifico di dominio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
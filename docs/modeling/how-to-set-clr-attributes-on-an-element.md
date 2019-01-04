---
title: 'Procedura: Impostare gli attributi CLR in un elemento'
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
ms.prod: visual-studio-dev15
ms.openlocfilehash: 5b9a96f70febc6a33d80557a09cc8bc8e1adf2f4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53938082"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Procedura: Impostare gli attributi CLR in un elemento
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

- [Glossario sugli strumenti Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
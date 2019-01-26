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
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 54b4340fe72552f3287a5c6ebec55c9c9d326ac1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54932272"
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

     `[` *AttributeName* `(` *ParameterName* `=` *Type* `)]`

## <a name="see-also"></a>Vedere anche

- [Glossario sugli strumenti Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
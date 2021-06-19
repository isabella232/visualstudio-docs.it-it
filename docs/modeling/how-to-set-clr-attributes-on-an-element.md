---
title: 'Procedura: impostare gli attributi CLR in un elemento'
description: Informazioni su come aggiungere qualsiasi attributo che eredita dalla classe System.Attribute.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b11a6bd4a04bdb469cdf5c2fe2d7b78e0c0fe29a
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387333"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Procedura: impostare gli attributi CLR in un elemento
Gli attributi personalizzati sono attributi speciali che possono essere aggiunti a elementi di dominio, forme, connettori e diagrammi. È possibile aggiungere qualsiasi attributo che eredita dalla `System.Attribute` classe .

### <a name="to-add-a-custom-attribute"></a>Per aggiungere un attributo personalizzato

1. In **DSL Explorer** selezionare l'elemento a cui si vuole aggiungere un attributo personalizzato.

2. Nella finestra **Proprietà** fare  clic sull'icona Sfoglia (**...**) accanto alla proprietà Attributi personalizzati.

     Verrà **visualizzata la finestra** di dialogo Modifica attributi .

3. Nella colonna **Nome** fare clic **\<add attribute>** su e digitare il nome dell'attributo. Premere INVIO.

4. La riga sotto il nome dell'attributo mostra le parentesi. In questa riga digitare un tipo di parametro per l'attributo ,ad esempio `string` , quindi premere INVIO.

5. Nella colonna **Proprietà nome** digitare un nome appropriato, ad esempio `MyString` .

6. Fare clic su **OK**.

     La **proprietà Attributi** personalizzati ora visualizza l'attributo nel formato seguente:

     `[`*AttributeName* `(` *ParameterName* `=` *Tipo*`)]`

## <a name="see-also"></a>Vedi anche

- [Glossario di Strumenti Domain-Specific Language](/previous-versions/bb126564(v=vs.100))
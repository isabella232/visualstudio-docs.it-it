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
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: b6b11d186ea6c4831679c111a632ffe710a6b886
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122143365"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Procedura: impostare gli attributi CLR in un elemento
Gli attributi personalizzati sono attributi speciali che possono essere aggiunti a elementi di dominio, forme, connettori e diagrammi. È possibile aggiungere qualsiasi attributo che eredita dalla `System.Attribute` classe .

### <a name="to-add-a-custom-attribute"></a>Per aggiungere un attributo personalizzato

1. In **Esplora DSL** selezionare l'elemento a cui si vuole aggiungere un attributo personalizzato.

2. Nella finestra **Proprietà** fare clic sull'icona Sfoglia (**...**) accanto alla proprietà **Attributi** personalizzati.

     Verrà **visualizzata la finestra** di dialogo Modifica attributi .

3. Nella colonna **Nome** fare clic su **\<add attribute>** e digitare il nome dell'attributo. Premere INVIO.

4. La riga sotto il nome dell'attributo mostra le parentesi. In questa riga digitare un tipo di parametro per l'attributo , ad esempio `string` , e quindi premere INVIO.

5. Nella colonna **Proprietà nome** digitare un nome appropriato, ad esempio `MyString` .

6. Fare clic su **OK**.

     La **proprietà Attributi** personalizzati visualizza ora l'attributo nel formato seguente:

     `[`*AttributeName* `(` *ParameterName* `=` *Tipo*`)]`

## <a name="see-also"></a>Vedi anche

- [Glossario di Strumenti Domain-Specific Language](/previous-versions/bb126564(v=vs.100))
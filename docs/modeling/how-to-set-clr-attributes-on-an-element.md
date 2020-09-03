---
title: 'Procedura: impostare gli attributi CLR in un elemento'
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ebda963bf1afa55fa8d7f98774c72a75d242ceef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85532457"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Procedura: impostare gli attributi CLR in un elemento
Gli attributi personalizzati sono attributi speciali che possono essere aggiunti a elementi di dominio, forme, connettori e diagrammi. È possibile aggiungere qualsiasi attributo che erediti dalla `System.Attribute` classe.

### <a name="to-add-a-custom-attribute"></a>Per aggiungere un attributo personalizzato

1. In **DSL Explorer**selezionare l'elemento a cui si desidera aggiungere un attributo personalizzato.

2. Nella finestra **Proprietà** fare clic sull'icona Sfoglia (**..**.) accanto alla proprietà **attributi personalizzati** .

     Verrà visualizzata la finestra di dialogo **modifica attributi** .

3. Nella colonna **nome** fare clic **\<add attribute>** e digitare il nome dell'attributo. Premere INVIO.

4. La riga sotto il nome dell'attributo Mostra le parentesi. In questa riga digitare un tipo di parametro per l'attributo (ad esempio, `string` ) e quindi premere INVIO.

5. Nella colonna **proprietà nome** Digitare un nome appropriato, ad esempio `MyString` .

6. Fare clic su **OK**.

     La proprietà **attributi personalizzati** ora Visualizza l'attributo nel formato seguente:

     `[`*AttributeName* `(` *Parametroname* `=` *Tipo* di`)]`

## <a name="see-also"></a>Vedere anche

- [Glossario di Strumenti Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
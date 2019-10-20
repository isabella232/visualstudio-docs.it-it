---
title: 'Procedura: impostare gli attributi CLR in un elemento | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
ms.assetid: b3db3c74-920c-4701-9544-6f75cbe8b7c9
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 72ad9175729451c82fca3b61d06e449edaf8cf38
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662548"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Procedura: impostare gli attributi CLR in un elemento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gli attributi personalizzati sono attributi speciali che possono essere aggiunti a elementi di dominio, forme, connettori e diagrammi. È possibile aggiungere qualsiasi attributo che erediti dalla classe `System.Attribute`.

### <a name="to-add-a-custom-attribute"></a>Per aggiungere un attributo personalizzato

1. In **DSL Explorer**selezionare l'elemento a cui si desidera aggiungere un attributo personalizzato.

2. Nella finestra **Proprietà** fare clic sull'icona Sfoglia ( **..** .) accanto alla proprietà **attributi personalizzati** .

     Verrà visualizzata la finestra di dialogo **modifica attributi** .

3. Nella colonna **nome** fare clic su **\<add attributo >** e digitare il nome dell'attributo. Premere INVIO.

4. La riga sotto il nome dell'attributo Mostra le parentesi. In questa riga digitare un tipo di parametro per l'attributo, ad esempio `string`, quindi premere INVIO.

5. Nella colonna **proprietà nome** Digitare un nome appropriato, ad esempio `MyString`.

6. Fare clic su **OK**.

     La proprietà **attributi personalizzati** ora Visualizza l'attributo nel formato seguente:

     `[` *attributename* `(` *parametroname* `=` *tipo* `)]`

## <a name="see-also"></a>Vedere anche
 [Glossario di Strumenti Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)

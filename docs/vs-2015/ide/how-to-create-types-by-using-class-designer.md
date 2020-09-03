---
title: 'Procedura: Creare tipi tramite Progettazione classi | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.Clr.ClrAttributesDialog
helpviewer_keywords:
- custom attributes, applying
- class diagrams, creating types
- classes [Visual Studio], creating with Class Designer
- Class Designer [Visual Studio], creating classes
- types [Visual Studio], class diagrams
- attributes [Visual Studio], applying custom
ms.assetid: 94458c31-28bc-40e2-9737-85868788a0e5
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f87e3a3adda270f6b78b9134c7535bda6c73d952
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85533146"
---
# <a name="how-to-create-types-by-using-class-designer"></a>Procedura: creare tipi utilizzando Progettazione classi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per progettare nuovi tipi per progetti Visual C# .NET e Visual Basic .NET, crearli in un diagramma di classi. Per visualizzare i tipi esistenti, vedere [Procedura: Visualizzare i tipi esistenti (Progettazione classi)](../ide/how-to-view-existing-types-class-designer.md).

- [Crea un nuovo tipo](#CreateType)

- [Applicare un attributo personalizzato a un tipo](#CustAttributeType)

- [Applicare un attributo personalizzato a un membro di un tipo](#CustAttributeMember)

## <a name="create-a-new-type"></a><a name="CreateType"></a> Crea un nuovo tipo

1. In Progettazione classi di Casella degli strumenti trascinare uno dei seguenti elementi in un diagramma di classi:

    - **Classe** o **Classe astratta**

    - **Enumerazione**

    - **Interfaccia**

    - **Struttura** (VB) o **Struct** (C#)

    - **Delegato**

    - **Modulo** (solo VB)

2. Assegnare un nome al tipo. Selezionare quindi il relativo livello di accesso.

3. Selezionare il file in cui si desidera aggiungere il codice iniziale per il tipo:

    - Per creare un nuovo file e aggiungerlo al progetto corrente, selezionare **Crea nuovo file** e assegnare un nome al file.

    - Per aggiungere codice a un file esistente, selezionare **Aggiungi a file esistente**.

         Se la soluzione contiene un progetto che condivide il codice tra più app, è possibile aggiungere un nuovo tipo a un diagramma di classi nel progetto di app, ma solo se il file di classe corrispondente si trova nello stesso progetto di app o nel progetto condiviso.

4. Aggiungere ora altri elementi per definire il tipo:

    |**Per**|**Aggiungere**|
    |-|-|
    |Classi, classi astratte, strutture o struct|Metodi, proprietà, campi, eventi, costruttori (metodo), distruttori (metodo) e costanti che definiscono il tipo|
    |Enumerazioni|Valori di campo che costituiscono l'enumerazione|
    |Interfacce|Metodi, proprietà ed eventi che costituiscono l'interfaccia|
    |Delegato|Parametri che definiscono il delegato|
    |Modulo|Metodi, proprietà, campi, eventi, costruttori (metodo), distruttori (metodo) e costanti che definiscono il modulo|

     Vedere [Creazione di membri](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers).

## <a name="apply-a-custom-attribute-to-a-type"></a><a name="CustAttributeType"></a> Applicare un attributo personalizzato a un tipo

1. Fare clic sulla forma del tipo in un diagramma classi.

2. Nella finestra Proprietà fare clic sul pulsante con i puntini di sospensione (...) accanto alla proprietà **Attributi personalizzati** relativa al tipo.

3. Aggiungere uno o più attributi personalizzati, uno per riga. Non racchiuderli tra parentesi.

     Al termine, gli attributi personalizzati verranno applicati al tipo.

## <a name="apply-a-custom-attribute-to-a-type-member"></a><a name="CustAttributeMember"></a> Applicare un attributo personalizzato a un membro di tipo

1. Fare clic sul nome del membro nella forma del relativo tipo in un diagramma classi oppure nella relativa riga nella finestra Dettagli classe.

2. Nella finestra Proprietà individuare la proprietà **Attributi personalizzati** del membro.

3. Aggiungere uno o più attributi personalizzati, uno per riga. Non racchiuderli tra parentesi.

     Al termine, gli attributi personalizzati verranno applicati al tipo.

## <a name="see-also"></a>Vedere anche
 [Procedura: creare ereditarietà tra tipi (Progettazione classi)](../ide/how-to-create-inheritance-between-types-class-designer.md) [procedura: creare associazioni tra tipi (Progettazione classi)](../ide/how-to-create-associations-between-types-class-designer.md) [creazione e configurazione di membri di tipi (Progettazione classi)](../ide/creating-and-configuring-type-members-class-designer.md) [utilizzo di diagrammi classi (Progettazione classi) progettazione di](../ide/working-with-class-diagrams-class-designer.md) [classi e tipi (Progettazione classi)](../ide/designing-classes-and-types-class-designer.md)

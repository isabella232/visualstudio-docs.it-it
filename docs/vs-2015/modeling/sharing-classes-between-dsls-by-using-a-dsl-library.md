---
title: Condivisione di classi tra DSLs usando una libreria DSL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 509bd96b-3e66-47f4-8642-771421d0d0d5
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 093cc277fa1cbe1915099fd9663fc1ccb797ca3a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671174"
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>Condivisione di classi tra DSL utilizzando una libreria DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nell' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] SDK di visualizzazione e modellazione è possibile creare una definizione DSL incompleta che è possibile importare in un altro linguaggio DSL. In questo modo è possibile fattorizzare parti comuni di modelli simili.

## <a name="creating-and-using-dsl-libraries"></a>Creazione e utilizzo di librerie DSL

#### <a name="to-create-a-dsl-library"></a>Per creare una libreria DSL

1. Creare un nuovo progetto DSL e scegliere il modello di soluzione libreria DSL.

     Un progetto DSL singolo verrà creato con un modello vuoto.

2. È possibile aggiungere classi di dominio, relazioni, forme e così via.

     Gli elementi nella libreria non devono formare un singolo albero di incorporamento.

     Per definire una relazione che può essere utilizzata dagli utilità di importazione, creare due classi di dominio e creare la relazione tra di esse.

     Si consiglia di impostare il **modificatore di ereditarietà** delle classi di dominio su `Abstract` .

3. È possibile aggiungere elementi definiti in DSL Explorer, ad esempio i generatori di connessioni.

4. È possibile aggiungere personalizzazioni che richiedono codice aggiuntivo, ad esempio i vincoli di convalida.

5. Fare clic su **trasforma tutti i modelli**.

6. Compilare il progetto.

7. Quando si distribuisce il linguaggio DSL per l'uso da parte di altri utenti, è necessario specificare sia l'assembly compilato (DLL) che il file `DslDefinition.dsl` . È possibile trovare l'assembly compilato in una cartella in `Dsl\bin\*`

#### <a name="to-import-a-dsl-library"></a>Per importare una libreria DSL

1. In un'altra definizione DSL, in **DSL Explorer**, fare clic con il pulsante destro del mouse sulla classe radice del DSL, quindi scegliere **Aggiungi nuova importazione DslLibrary**.

2. Nella Finestra Proprietà impostare il percorso del **file** della libreria. È possibile usare un percorso relativo o assoluto.

    La libreria importata viene visualizzata in DSL Explorer, in modalità di sola lettura.

3. È possibile utilizzare le classi importate come classi di base. Creare una classe di dominio nel DSL di importazione e, nel Finestra Proprietà, impostare la **classe di base** su una classe importata.

4. Fare clic su Trasforma tutti i modelli.

5. Aggiungere al progetto DSL un riferimento all'assembly (DLL) compilato dal progetto libreria DSL.

6. Compilare la soluzione.

   Una libreria DSL può importare altre librerie. Quando si importa una libreria, anche le relative importazioni vengono visualizzate automaticamente in Esplora DSL.

## <a name="see-also"></a>Vedere anche
 [Come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md)

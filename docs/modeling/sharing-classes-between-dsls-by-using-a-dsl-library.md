---
title: Condivisione di classi tra DSL utilizzando una libreria DSL
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4bfadc1777dfb4ba0c8ea712cfd39becc47f54a1
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2020
ms.locfileid: "76111357"
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>Condivisione di classi tra DSL utilizzando una libreria DSL
Nell'SDK di visualizzazione e modellazione di Visual Studio è possibile creare una definizione DSL incompleta che è possibile importare in un altro linguaggio DSL. In questo modo è possibile fattorizzare parti comuni di modelli simili.

## <a name="creating-and-using-dsl-libraries"></a>Creazione e utilizzo di librerie DSL

#### <a name="to-create-a-dsl-library"></a>Per creare una libreria DSL

1. Creare un nuovo progetto DSL e scegliere il modello di soluzione libreria DSL.

     Un progetto DSL singolo verrà creato con un modello vuoto.

2. È possibile aggiungere classi di dominio, relazioni, forme e così via.

     Gli elementi nella libreria non devono formare un singolo albero di incorporamento.

     Per definire una relazione che può essere utilizzata dagli utilità di importazione, creare due classi di dominio e creare la relazione tra di esse.

     Si consiglia di impostare il **modificatore di ereditarietà** delle classi di dominio su `Abstract`.

3. È possibile aggiungere elementi definiti in DSL Explorer, ad esempio i generatori di connessioni.

4. È possibile aggiungere personalizzazioni che richiedono codice aggiuntivo, ad esempio i vincoli di convalida.

5. Fare clic su **Trasforma tutti i modelli**.

6. Compilazione del progetto.

7. Quando si distribuisce il linguaggio DSL per l'uso da parte di altri utenti, è necessario specificare sia l'assembly compilato (DLL) che il file `DslDefinition.dsl`. È possibile trovare l'assembly compilato in una cartella `Dsl\bin\*`

#### <a name="to-import-a-dsl-library"></a>Per importare una libreria DSL

1. In un'altra definizione DSL, in **DSL Explorer**, fare clic con il pulsante destro del mouse sulla classe radice del DSL, quindi scegliere **Aggiungi nuova importazione DslLibrary**.

2. Nella Finestra Proprietà impostare il percorso del **file** della libreria. È possibile usare un percorso relativo o assoluto.

    La libreria importata viene visualizzata in DSL Explorer, in modalità di sola lettura.

3. È possibile utilizzare le classi importate come classi di base. Creare una classe di dominio nel DSL di importazione e, nel Finestra Proprietà, impostare la **classe di base** su una classe importata.

4. Fare clic su Trasforma tutti i modelli.

5. Aggiungere al progetto DSL un riferimento all'assembly (DLL) compilato dal progetto libreria DSL.

6. Compila la soluzione.

   Una libreria DSL può importare altre librerie. Quando si importa una libreria, anche le relative importazioni vengono visualizzate automaticamente in Esplora DSL.

## <a name="see-also"></a>Vedere anche

- [Come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

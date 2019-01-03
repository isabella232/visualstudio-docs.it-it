---
title: Condivisione di classi tra DSL utilizzando una libreria DSL
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: f95cc7fad1b4aaac3da687352cf5561a7d72ff8e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53897839"
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>Condivisione di classi tra DSL utilizzando una libreria DSL
In Visual Studio Visualization and Modeling SDK è possibile creare una definizione DSL incompleta che è possibile importare in un altro linguaggio specifico di dominio. Ciò consente di scomporre le parti comuni dei modelli simili.

## <a name="creating-and-using-dsl-libraries"></a>Creare e utilizzare le librerie DSL

#### <a name="to-create-a-dsl-library"></a>Per creare una libreria DSL

1.  Creare un nuovo progetto DSL e scegliere il modello di soluzione della libreria DSL.

     Verrà creato un singolo progetto DSL con un modello vuoto.

2.  È possibile aggiungere classi di dominio, relazioni, forme e così via.

     Gli elementi nella raccolta non è in modo da formare un singolo albero di incorporamento.

     Per definire una relazione che è possibile usare unità di importazione, creare due classi di dominio e creare la relazione tra di essi.

     È consigliabile impostare il **modificatore di ereditarietà** delle classi di dominio per `Abstract`.

3.  È possibile aggiungere gli elementi che definiscono in Esplora DSL, ad esempio i generatori di connessioni.

4.  È possibile aggiungere personalizzazioni che richiedono codice aggiuntivo, ad esempio i vincoli di convalida.

5.  Fare clic su **Trasforma tutti i modelli**.

6.  Compilare il progetto.

7.  Quando si distribuisce il linguaggio DSL per uso ad altri utenti, è necessario specificare sia l'assembly compilato (DLL) e il file `DslDefinition.dsl`. È possibile trovare l'assembly compilato in una cartella sotto `Dsl\bin\*`

#### <a name="to-import-a-dsl-library"></a>Per importare una libreria DSL

1. In un'altra definizione DSL, nella **DSL Explorer**, fare doppio clic la classe radice del DSL e quindi fare clic su **Aggiungi nuova importazione di DslLibrary**.

2. Nella finestra Proprietà impostare il **percorso File** della libreria. È possibile usare un percorso assoluto o relativo.

    La libreria importata viene visualizzato in Esplora DSL, in modalità di sola lettura.

3. È possibile utilizzare le classi importate come classi di base. Creare una classe di dominio nel DSL l'importazione e nelle proprietà della finestra, impostare **classe di base** a una classe importata.

4. Fare clic su Trasforma tutti i modelli.

5. Aggiungere al progetto DSL un riferimento all'assembly (DLL) che è stato compilato dal progetto di libreria DSL.

6. Compilare la soluzione.

   Una libreria DSL è possibile importare altre librerie. Quando si importa una libreria, in DSL Explorer vengono visualizzati automaticamente anche le relative importazioni.

## <a name="see-also"></a>Vedere anche

- [Come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

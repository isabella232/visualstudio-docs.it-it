---
title: Condivisione di classi tra DSL utilizzando una libreria DSL
description: In Visual Studio Visualization and Modeling SDK è possibile creare una definizione DSL incompleta che è possibile importare in un altro DSL.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 7b4f6deca3320a5c2182030d8e5cdec99a36c023
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637428"
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>Condivisione di classi tra DSL utilizzando una libreria DSL
In Visual Studio Visualization and Modeling SDK è possibile creare una definizione DSL incompleta che è possibile importare in un altro DSL. In questo modo è possibile eseguire il factor di parti comuni di modelli simili.

## <a name="creating-and-using-dsl-libraries"></a>Creazione e uso di librerie DSL

#### <a name="to-create-a-dsl-library"></a>Per creare una libreria DSL

1. Creare un nuovo progetto DSL e scegliere il modello di soluzione Libreria DSL.

     Verrà creato un singolo progetto DSL con un modello vuoto.

2. È possibile aggiungere classi di dominio, relazioni, forme e così via.

     Non è necessario che gli elementi nella libreria formino un singolo albero di incorporamento.

     Per definire una relazione che le utilità di importazione possono usare, creare due classi di dominio e creare la relazione tra di esse.

     Provare a impostare il **modificatore di ereditarietà** delle classi di dominio su `Abstract` .

3. È possibile aggiungere elementi definiti in Esplora DSL, ad esempio generatori di connessioni.

4. È possibile aggiungere personalizzazioni che richiedono codice aggiuntivo, ad esempio vincoli di convalida.

5. Fare clic **su Trasforma tutti i modelli**.

6. Compilare il progetto.

7. Quando si distribuisce il DSL per l'uso da parte di altri utenti, è necessario fornire sia l'assembly compilato (DLL) che il file `DslDefinition.dsl` . È possibile trovare l'assembly compilato in una cartella in `Dsl\bin\*`

#### <a name="to-import-a-dsl-library"></a>Per importare una libreria DSL

1. In un'altra definizione **DSL, in DSL Explorer,** fare clic con il pulsante destro del mouse sulla classe radice del DSL e quindi scegliere Aggiungi nuovo **DslLibrary Import**.

2. Nella finestra Finestra Proprietà impostare il **percorso file** della libreria. È possibile usare un percorso relativo o assoluto.

    La libreria importata viene visualizzata in Esplora DSL, in modalità di sola lettura.

3. È possibile usare le classi importate come classi di base. Creare una classe di dominio nel DSL di importazione e nella Finestra Proprietà impostare **Classe base** su una classe importata.

4. Fare clic su Trasforma tutti i modelli.

5. Aggiungere al progetto DSL un riferimento all'assembly (DLL) compilato dal progetto libreria DSL.

6. Compilare la soluzione.

   Una libreria DSL può importare altre librerie. Quando si importa una libreria, anche le relative importazioni vengono visualizzate automaticamente in Esplora DSL.

## <a name="see-also"></a>Vedi anche

- [Come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

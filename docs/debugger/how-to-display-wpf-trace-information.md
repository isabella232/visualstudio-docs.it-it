---
title: Visualizzare informazioni di traccia WPF | Microsoft Docs
description: Visual Studio possibile ricevere informazioni di traccia di debug dalle applicazioni WPF e visualizzarle nella finestra Output. Informazioni su come gestire e personalizzare la traccia WPF.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: be3c6859-06e1-459e-9fd0-46375b5f55ef
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 6b697645cbff18ebb7053f1b9facca221de767d0
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636691"
---
# <a name="how-to-display-wpf-trace-information"></a>Procedura: visualizzare le informazioni di traccia WPF
[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] è in grado di ricevere informazioni di traccia di debug da applicazioni WPF e di visualizzare tali informazioni nella finestra **Output**. Per visualizzare le informazioni di traccia di debug, la tracciatura WPF deve essere abilitata.

 È possibile abilitare la tracciatura WPF nel file App.Config o a livello di codice utilizzando la classe <xref:System.Diagnostics.PresentationTraceSources>. Un modo più semplice per abilitare la tracciatura WPF è quello di utilizzare la finestra **Opzioni**. La tracciatura WPF per applicazioni Web non è supportata.

### <a name="to-enable-or-customize-wpf-trace-information"></a>Per abilitare o personalizzare le informazioni di traccia WPF

1. Scegliere **Options** (Opzioni) dal menu **Tools** (Strumenti).

2. Nella finestra di dialogo **Opzioni** aprire il nodo **Debug** nella casella sulla sinistra.

3. In **Debug** fare clic su **Finestra di output**.

4. In **Impostazioni generali di output** selezionare **Tutto l'output di debug**.

5. Nella casella sulla destra cercare **Impostazioni di traccia WPF**.

6. Aprire il nodo **Impostazioni di traccia WPF**.

7. In **Impostazioni di traccia WPF** fare clic sulla categoria di impostazioni che si desidera abilitare, ad esempio **data binding**.

     Verrà visualizzato un controllo elenco a discesa nella colonna Impostazioni accanto a **Data binding** o qualsiasi categoria selezionata.

8. Fare clic sull'elenco a discesa e selezionare il tipo di informazioni di traccia che si vuole visualizzare: **Tutto**, **Critico**, **Errore**, **Avviso**, **Informazioni**, **Dettaglio** o **Attività**.

     **Critico** abilita solo la tracciatura di eventi Critico.

     **Errore** abilita la tracciatura di eventi Critico ed Errore.

     **Avviso** abilita la tracciatura di eventi Critico, Errore e Avviso.

     **Informazioni** abilita la tracciatura di eventi Critico, Errore, Avviso e Informazioni.

     **Dettaglio** abilita la tracciatura di eventi Critico, Errore, Avviso, Informazione e Dettaglio.

     **Attività** abilita la tracciatura di eventi Interrompi, Avvia, Sospendi, Trasferisci e Riprendi.

     Per ulteriori informazioni sul significato di questi livelli di informazioni di traccia, vedere <xref:System.Diagnostics.SourceLevels>.

9. Fare clic su **OK**.

### <a name="to-disable-wpf-trace-information"></a>Per disabilitare le informazioni di traccia WPF

1. Scegliere **Options** (Opzioni) dal menu **Tools** (Strumenti).

2. Nella finestra di dialogo **Opzioni** aprire il nodo **Debug** nella casella sulla sinistra.

3. In **Debug** fare clic su **Finestra di output**.

4. Nella casella sulla destra cercare **Impostazioni di traccia WPF**.

5. Aprire il nodo **Impostazioni di traccia WPF**.

6. In **Impostazioni di traccia WPF** fare clic sulla categoria di impostazioni che si desidera abilitare, ad esempio **data binding**.

     Verrà visualizzato un controllo elenco a discesa nella colonna Impostazioni accanto a **Data binding** o qualsiasi categoria selezionata.

7. Fare clic sull'elenco a discesa e selezionare **Disattivato**.

8. Fare clic su **OK**.

## <a name="see-also"></a>Vedi anche
- [Debug di WPF](../debugger/debugging-wpf.md)
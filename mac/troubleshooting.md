---
title: Risoluzione dei problemi di Visual Studio per Mac
description: Problemi comuni e risoluzioni per Visual Studio per gli utenti Mac.
ms.topic: troubleshooting
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: CE860D79-E29E-4B93-B094-BE74B35FC1C2
ms.openlocfilehash: 6d8edc7942b460c4c11e20bc9a0c5cae204328cf
ms.sourcegitcommit: 2597236a481afbaf1ad4915743898ee1aee49760
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/10/2018
ms.locfileid: "43224453"
---
# <a name="troubleshooting"></a>Risoluzione dei problemi

## <a name="viewing-logs-in-visual-studio-for-mac"></a>Visualizzazione dei log in Visual Studio per Mac

Per trovare i log, spostarsi sulla voce di menu **Guida > Apri directory log** come illustrato di seguito:

![Voce di menu Apri directory log](media/troubleshooting-image1.png)

## <a name="viewing-exceptions"></a>Visualizzazione delle eccezioni

Quando viene rilevata un'eccezione, viene visualizzato un fumetto. Per visualizzare ulteriori dettagli, selezionare il pulsante **Visualizza dettagli**:

![Visualizzare ulteriori dettagli su un'eccezione](media/troubleshooting-image2.png)

Verrà visualizzata la finestra di dialogo **Mostra dettagli** che include ulteriori informazioni sull'eccezione:

![Finestra di dialogo Mostra dettagli](media/troubleshooting-image3.png)

Le sezioni importanti della finestra di dialogo numerate sopra sono descritte in dettaglio di seguito:

1. Tipo di eccezione che mostra il nome completo del tipo di eccezione osservato.
2. Messaggio di eccezione che mostra il valore della proprietà Message dell'oggetto eccezione.
3. Il tipo di eccezione Inner che mostra il nome completo del tipo di eccezione per l'eccezione attualmente selezionata nella visualizzazione struttura ad albero delle eccezioni Inner.
4. Il messaggio dell'eccezione Inner che mostra il valore della proprietà Message dell'eccezione selezionata nella visualizzazione struttura ad albero delle eccezioni Inner.
5. Visualizzazione StackTrace. Può essere compressa tramite una freccia di divulgazione e contiene voci di stack frame.
6. Esempio di voci di codice non utente.
7. Esempio di voci di codice utente.
8. Visualizzazione delle proprietà che mostra tutte le proprietà e i campi dell'eccezione. Può essere compressa tramite una freccia di divulgazione.
9. Visualizzazione struttura ad albero delle eccezioni Inner. Selezionare le eccezioni Inner in questa visualizzazione tramite le frecce su e giù oppure con il mouse o il trackpad.
10. Per impostazione predefinita, questa opzione è impostata in base a come è impostata l'opzione **Esegui solo il debug del codice del progetto** nelle impostazioni del debugger. Se si seleziona questa casella, si consentirà di comprimere tutto il codice non utente in una sola riga in StackTrace.
11. Pulsante di copia che consente di copiare l'output di `exception.ToString()` negli Appunti.

Notare che solo alcune sezioni saranno visibili quando l'eccezione ha un'eccezione Inner.
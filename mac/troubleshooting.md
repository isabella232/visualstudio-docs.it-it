---
title: Risoluzione dei problemi di Visual Studio per Mac
description: Problemi comuni e risoluzioni per Visual Studio per gli utenti Mac.
ms.topic: troubleshooting
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.assetid: CE860D79-E29E-4B93-B094-BE74B35FC1C2
ms.openlocfilehash: a802bf950b5f759a41f88fb9260449fadcea8974
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="troubleshooting"></a>Risoluzione dei problemi

## <a name="viewing-logs-in-visual-studio-for-mac"></a>Visualizzazione dei log in Visual Studio per Mac

Per trovare i log, spostarsi sulla voce di menu **Guida > Apri directory log** come illustrato di seguito:

![Voce di menu Apri directory log](media/troubleshooting-image1.png)

## <a name="viewing-exceptions"></a>Visualizzazione delle eccezioni

Quando viene rilevata un'eccezione, viene visualizzato un fumetto. Per visualizzare ulteriori dettagli, selezionare il pulsante **Visualizza dettagli**:

![Visualizzare ulteriori dettagli su un'eccezione](media/troubleshooting-image2.png)

Verrà visualizzata la finestra di dialogo **Mostra dettagli** che include ulteriori informazioni sull'eccezione:

![](media/troubleshooting-image3.png)

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
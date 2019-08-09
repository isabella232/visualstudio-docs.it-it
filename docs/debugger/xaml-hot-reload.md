---
title: Scrivere ed eseguire il debug di XAML usando il ricaricamento a caldo di XAML
description: Il ricaricamento a caldo di XAML o la modifica e la continuazione di XAML consente di apportare modifiche al codice XAML durante l'esecuzione delle app
ms.date: 08/05/2019
ms.topic: conceptual
helpviewer_keywords:
- xaml edit and continue
- xaml hot reload
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0acacac883153990861385c96eeb3379c464f97f
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68870995"
---
# <a name="write-and-debug-running-xaml-code-with-xaml-hot-reload-in-visual-studio"></a>Scrivere ed eseguire il debug del codice XAML in esecuzione con il ricaricamento a caldo di XAML in Visual Studio

Il ricaricamento a caldo di XAML consente di compilare l'interfaccia utente dell'app WPF o UWP consentendo di apportare modifiche al codice XAML durante l'esecuzione dell'app. Il ricaricamento a caldo è disponibile sia in Visual Studio che in Blend per Visual Studio. Questa funzionalità consente di compilare e testare in modo incrementale il codice XAML con il vantaggio del contesto dei dati dell'app in esecuzione, dello stato di autenticazione e di altre complessità reali che è difficile simulare in fase di progettazione.

Il ricaricamento a caldo di XAML è particolarmente utile in questi scenari:

* Correzione dei problemi dell'interfaccia utente rilevati nel codice XAML dopo l'avvio dell'app in modalità di debug.

* Creazione di un nuovo componente dell'interfaccia utente per un'app in fase di sviluppo, sfruttando al contempo il contesto di runtime dell'app.

|Tipi di applicazioni supportati|Sistema operativo e strumenti|
|-|-|-|
|Windows Presentation Foundation (WPF) |.NET Framework 4.6+</br>Windows 7 e versioni successive |
|App di Windows universale (UWP)|Windows 10 e versioni successive, con [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 14393 + |

> [!NOTE]
> Il ricaricamento a caldo in XAML di Visual Studio è attualmente supportato solo quando si esegue l'applicazione in Visual Studio o Blend per Visual Studio con il debugger collegato (**F5** o **avviare il debug**). Non è possibile abilitare questa esperienza utilizzando [Connetti a processo](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

## <a name="known-limitations"></a>Limitazioni note

Di seguito sono riportate le limitazioni note del ricaricamento a caldo di XAML. Per aggirare le limitazioni che si verificano, arrestare il debugger, quindi completare l'operazione.

|Limitazione|WPF|UWP|Note|
|-|-|-|-|
|Cablare gli eventi ai controlli durante l'esecuzione dell'app|Non supportato|Non supportate|Vedere errore: *Verifica evento non riuscita*|
|Creazione di oggetti risorsa in un dizionario risorse, ad esempio quelli nella pagina/finestra o nel file *app. XAML* dell'app.|Non supportato|Supportato|Esempio: aggiunta di `SolidColorBrush` un oggetto a un dizionario risorse da utilizzare `StaticResource`come.</br>Nota: È possibile applicare/utilizzare risorse statiche, convertitori di stile e altri elementi scritti in un dizionario risorse durante l'utilizzo del ricaricamento a caldo di XAML. Solo la creazione della risorsa non è supportata.</br> Modifica della proprietà del `Source` dizionario risorse.|
|Aggiunta di nuovi controlli, classi, finestre o altri file al progetto durante l'esecuzione dell'app|Non supportato|Non supportato|Nessuna|
|Gestione dei pacchetti NuGet (aggiunta/rimozione/aggiornamento di pacchetti)|Non supportato|Non supportato|Nessuna|
|Modifica data binding che usa l'estensione di markup {x:Bind}|N/D|Supportato in Visual Studio 2019 e versioni successive|Non supportato in Visual Studio 2017 o versioni precedenti|

## <a name="error-messages"></a>messaggi di errore

È possibile che si verifichino gli errori seguenti durante l'utilizzo del ricaricamento a caldo di XAML.

|Messaggio di errore|Descrizione|
|-|-|
|Verifica evento non riuscita|Errore indica che si sta tentando di collegare un evento a uno dei controlli, che non è supportato mentre l'applicazione è in esecuzione.|
|La funzionalità Modifica e continuazione di XAML non ha trovato elementi da aggiornare.|Si verifica un errore durante la modifica del codice XAML che non è possibile aggiornare nell'app.</br> Questo errore può talvolta essere risolto usando l'app in esecuzione per passare a una visualizzazione in cui viene usato il codice XAML.</br> In alcuni casi, questo errore indica che non è possibile applicare la modifica specifica fino a quando non si riavvia la sessione di debug. |
|Questa modifica non è supportata durante una sessione di debug.|Errore indica che la modifica che si sta tentando di eseguire non è supportata dal ricaricamento a caldo di XAML. Arrestare la sessione di debug, apportare la modifica e quindi riavviare la sessione di debug.|

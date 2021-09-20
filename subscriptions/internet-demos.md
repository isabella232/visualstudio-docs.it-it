---
title: Demo Internet tramite Servizi terminal nelle sottoscrizioni Visual Studio internet| Microsoft Docs
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: 1c5ede60-cb5a-4d5f-a6a2-a1f536f6c4ad
ms.date: 03/21/2021
ms.topic: conceptual
description: Informazioni sull'uso di codici Product Key per supportare dimostrazioni via Internet tramite Servizi terminal e abilitare l'accesso tramite Servizi Desktop remoto
ms.openlocfilehash: 0391de091cd3b836fbe38afce903b52584da4b5a
ms.sourcegitcommit: c2afe12aaf04456846613550b367cf86eb082f4b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2021
ms.locfileid: "128002311"
---
# <a name="internet-demonstrations-via-terminal-services"></a>Dimostrazioni via Internet tramite Servizi terminal
Con una sottoscrizione di Visual Studio è possibile offrire agli utenti finali l'accesso a dimostrazioni via Internet dei programmi tramite Servizi terminal (Windows Server 2003 o Windows Server 2008) o Servizi Desktop remoto (Windows Server 2008 R2 e versioni successive). In questo modo fino a 200 utenti anonimi potranno accedere contemporaneamente alla dimostrazione. La dimostrazione non deve contenere dati di produzione. I sottoscrittori di Visual Studio saranno autorizzati a illustrare le proprie applicazioni agli utenti finali. Questa dimostrazione via Internet mediante Servizi terminal (TS) e Servizi Desktop remoto (RDS) rappresenta l'unico scenario in cui gli utenti finali sprovvisti di sottoscrizione di Visual Studio potranno interagire con l'applicazione demo, mentre il software è concesso in licenza tramite sottoscrizione di Visual Studio.

Si tratta di un'aggiunta ai diritti di sviluppo/test, che consente ai sottoscrittori di Visual Studio di usare il numero necessario di connessioni Servizi Desktop remoto o Servizi terminal.

## <a name="enabling-rds-access"></a>Abilitazione dell'accesso tramite Servizi Desktop remoto
I sottoscrittori di Visual Studio possono aumentare il numero di utenti che sono autorizzati ad accedere a Windows Server tramite Servizi Desktop remoto immettendo un codice Product Key specificato nella scheda [Codici "Product Key"](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs) nel [portale sottoscrittore](https://my.visualstudio.com?wt.mc_id=o~msft~docs). Per ottenere un codice Product Key, connettersi alla pagina Codici "Product Key" e scorrere verso il basso fino a individuare la versione di Windows Server in esecuzione. Individuare la voce relativa alle connessioni di Servizi Desktop remoto < utente o dispositivo > di Windows Server < versione > R2 e quindi fare clic sul collegamento Claim Key (Richiedi codice Product Key). Ad esempio, se si usa Servizi Desktop remoto su Windows Server 2012 R2 e la distribuzione usa licenze CAL di tipo utente, scegliere la voce relativa alle connessioni di tipo utente di Servizi Desktop remoto di Windows Server 2012 (50).
Sono disponibili cinque codici di ogni tipo per Windows Server 2008 R2 e ogni codice supporterà 20 connessioni. Per Windows Server 2012 R2 sono disponibili quattro codici per ogni tipo e ogni codice supporterà 50 connessioni.

## <a name="to-enable-additional-connections-in-windows-server"></a>Per abilitare connessioni aggiuntive in Windows Server:
1. Aprire Server Manager.
2. Aprire l'elenco Server nel riquadro di spostamento a sinistra.
3. Fare clic con il pulsante destro del mouse sul server licenze e scegliere "Installa licenze".
4. Seguire i passaggi nella procedura guidata.  Quando si seleziona il tipo di contratto, scegliere "License Pack (per l'utente finale)" e immettere il codice Product Key ottenuto dal portale personale.

Gli utenti finali possono connettersi per accedere alle applicazioni tramite Servizi Desktop remoto, purché vengano soddisfatte le condizioni seguenti:
- Gli utenti devono essere anonimi (con stato non autenticato).
- Le connessioni devono essere effettuate su Internet.
- Fino a 200 connessioni utente simultanee possono essere usate per dimostrazioni dell'applicazione.
- I codici Product Key per abilitare le connessioni utente devono essere ottenuti da un sottoscrittore di Visual Studio.

## <a name="support-resources"></a>Risorse di supporto
- Per assistenza su vendite, sottoscrizioni, account e fatturazione per Sottoscrizioni di Visual Studio, contattare Visual Studio [supporto per le sottoscrizioni](https://aka.ms/vssubscriberhelp).

## <a name="see-also"></a>Vedi anche
- [Documentazione di Windows Server](/windows-server/)
- [Visual Studio documentazione](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Microsoft 365 documentazione](/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
Per materiale sussidiario sulla distribuzione di Servizi Desktop remoto, vedere la serie di blog in più parti sulla **distribuzione di sessioni di Servizi Desktop remoto 2012** all'indirizzo https://techcommunity.microsoft.com/t5/Ask-The-Performance-Team/bg-p/AskPerf. 

In caso di domande, visitare il [forum sui Servizi Desktop remoto Microsoft](https://social.technet.microsoft.com/Forums/windowsserver/home?forum=winserverTS).
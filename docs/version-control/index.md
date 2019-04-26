---
layout: LandingPage
title: Controllo della versione
description: Guida introduttiva al controllo della versione in Visual Studio
keywords: VSTS, TFS, controllo della versione
author: steved0x
ms.manager: jillfra
ms.author: sdanie
ms.date: 12/15/2017
ms.topic: landing-page
ms.prod: .net-core
ms.assetid: 2c119a5f-0272-48c0-8d6c-806196944aea
ms.workload:
- multiple
ms.openlocfilehash: 97facaed877030dca4a6a2257147c4d92201ab55
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62944929"
---
# <a name="version-control-in-visual-studio"></a>Controllo della versione in Visual Studio

I sistemi di controllo della versione consentono di tenere traccia delle modifiche al codice nel tempo. Quando si apportano modifiche, il sistema di controllo della versione crea uno snapshot dei file e lo salva in modo permanente in modo da poterlo richiamare in un secondo momento, se necessario. Visual Studio offre [Git](/azure/devops/repos/git/index?view=vsts) e il [controllo della versione di Team Foundation](/azure/devops/repos/tfvc/index?view=vsts). Per scegliere tra i due sistemi, vedere [Scelta del sistema di controllo della versione corretto](/azure/devops/repos/tfvc/comparison-git-tfvc?toc=/visualstudio/version-control/toc.json&bc=/azure/devops/repos/git/breadcrumb/vc/toc.json).

## <a name="git"></a>Git

Ad oggi, Git è il sistema di controllo della versione più diffuso e si sta affermando rapidamente come standard per il controllo della versione. Git è un sistema di controllo della versione distribuito e ciò significa che la copia locale del codice è un repository del controllo della versione completo. Questi repository locali completamente operativi semplificano il lavoro offline o remoto. Il commit del lavoro viene eseguito localmente e quindi la copia del repository viene sincronizzata con la copia nel server. Questo approccio è diverso rispetto al controllo della versione centralizzato, in cui i client devono sincronizzare il codice con un server prima di creare nuove versioni del codice.

<!-- markdownlint-disable MD033 -->
<ul class="panelContent cardsFTitle">
    <li>
        <a href="/azure/devops/git/what-is-git">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Informazioni su Git</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/azure/devops/repos/git/share-your-code-in-git-vs-2017">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Introduzione a Git in Visual Studio</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/azure/devops/repos/git/clone">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Clonare un repository Git esistente</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
</ul>

## <a name="tfvc"></a>TFVC

Controllo della versione di Team Foundation (TFVC) è un sistema di controllo della versione centralizzato. In genere, i membri del team hanno una sola versione di ogni file nel computer di sviluppo. I dati cronologici vengono gestiti solo sul server. I branch sono basati sul percorso e creati nel server.

<ul class="panelContent cardsFTitle">
    <li>
        <a href="/azure/devops/repos/tfvc/overview">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Informazioni sul controllo della versione di Team Foundation</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Introduzione al controllo della versione di Team Foundation in Visual Studio</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
   <li>
        <a href="/azure/devops/repos/tfvc/get-code-reviewed-vs">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Rivedere il codice</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
</ul>

## <a name="resources"></a>Risorse

- [Libro Pro Git](https://git-scm.com/book/en/v2)
- [Plan your migration to Git (Pianificare la migrazione a Git)](https://docs.microsoft.com/azure/devops/git/centralized-to-git)
- [Migrate from TFVC to Git (Eseguire la migrazione dal controllo della versione di Team Foundation a Git)](https://docs.microsoft.com/azure/devops/git/migrate-from-tfvc-to-git)
- [Controllo della versione (Visual Studio per Mac)](/visualstudio/mac/version-control)
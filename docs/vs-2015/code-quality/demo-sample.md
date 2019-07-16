---
title: Demo di esempio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: 9e85944e93b952b8239015761e8fb364cb265291
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201426"
---
# <a name="demo-sample"></a>Esempio dimostrativo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le procedure seguenti illustrano come creare un esempio per la [Procedura dettagliata: Analisi del codice C/C++ per i difetti](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md). Le procedure creano:  
  
- Oggetto [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] soluzione denominata CppDemo.  
  
- Un progetto di libreria statica con nome CodeDefects.  
  
- Un progetto di libreria statica con nome Annotations.  
  
  Le procedure forniscono inoltre il codice per i file di intestazione e. cpp per librerie statiche.  
  
### <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>Creare la soluzione CppDemo e il progetto CodeDefects  
  
1. Fare clic sul menu **File**, scegliere **Nuovo** e fare clic su **Nuovo progetto**.  
  
2. Nell'elenco ad albero **Tipo progetto** espandere **Altri linguaggi** se Visual C++ non è il linguaggio predefinito in Visual Studio.  
  
3. Espandere **Visual C++** , quindi fare clic su **Generale**.  
  
4. In **Modelli** fare clic su **Progetto vuoto**.  
  
5. Nella casella di testo **Nome** digitare **CodeDefects**.  
  
6. Selezionare la casella di controllo **Crea directory per soluzione**.  
  
7. Nella casella di testo **Nome soluzione** digitare **CppDemo**.  
  
### <a name="configure-the-codedefects-project-as-a-static-library"></a>Configurare il progetto CodeDefects come libreria statica  
  
1. In Esplora soluzioni fare clic con il pulsante destro del mouse su **CodeDefects** e fare clic su **Proprietà**.  
  
2. Espandere **Proprietà di configurazione** e fare clic su **Generale**.  
  
3. Nell'elenco **Generale** selezionare il testo nella colonna accanto a **Estensione di destinazione** e digitare **.lib**.  
  
4. In **Impostazioni predefinite progetto** fare clic sulla colonna accanto a **Tipo configurazione** e fare clic su **Libreria statica (.lib)** .  
  
### <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>Aggiungere l'intestazione e il file di origine al progetto CodeDefects  
  
1. In Esplora soluzioni espandere **CodeDefects**, fare clic con il pulsante destro del mouse su **File di intestazione**, fare clic su **Aggiungi** e quindi fare clic su **Nuovo elemento**.  
  
2. Nella finestra di dialogo **Aggiungi nuovo elemento** fare clic su **Codice** e quindi fare clic su **File di intestazione (.h)** .  
  
3. Nella casella **Nome** digitare **Bug.cpp** e quindi fare clic su **Aggiungi**.  
  
4. Copiare il codice seguente e incollarlo nella **bug. cpp** del file nei [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor.  
  
    ```  
    #include <windows.h>  
  
    //    
    //These 3 functions are consumed by the sample  
    //  but are not defined. This project cannot be linked!  
    //  
  
    bool CheckDomain( LPCSTR );  
    HRESULT ReadUserAccount();  
  
    //  
    //These constants define the common sizes of the   
    //  user account information throughout the program  
    //  
  
    const int USER_ACCOUNT_LEN = 256;  
    const int ACCOUNT_DOMAIN_LEN = 128;  
    ```  
  
5. In Esplora soluzioni fare clic con il pulsante destro del mouse su **File di origine**, scegliere **Nuovo** e quindi fare clic su **Nuovo elemento**.  
  
6. Nella finestra di dialogo **Aggiungi nuovo elemento** fare clic su **File di C++ (.cpp)** .  
  
7. Nella casella **Nome** digitare **Bug.cpp** e quindi fare clic su **Aggiungi**.  
  
8. Copiare il codice seguente e incollarlo nel file Bug.h nel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor.  
  
    ```  
    #include <stdlib.h>  
    #include "Bug.h"  
  
    // the user account   
    TCHAR g_userAccount[USER_ACCOUNT_LEN] = "";  
    int len = 0;  
  
    bool ProcessDomain()  
    {  
        TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];  
        // ReadUserAccount gets a 'domain\user' input from   
        //the user into the global 'g_userAccount'  
        if (ReadUserAccount() )  
        {  
  
            // Copies part of the string prior to the '\'   
            // character onto the 'domain' buffer  
            for( len = 0 ; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != '\0') ; len++  )  
            {  
                if ( g_userAccount[len] == '\\' )   
                {  
                    // Stops copying on the domain and user separator ('\')   
                    break;  
                }  
                domain[len] = g_userAccount[len];          
            }  
            if((len= ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
            {  
                // '\' was not found. Invalid domain\user string.  
                delete [] domain;  
                return false;  
            }  
            else  
            {  
                domain[len]='\0';  
            }  
            // Process domain string  
            bool result = CheckDomain( domain );  
  
            delete[] domain;  
            return result;  
        }  
        return false;  
    }  
  
    int path_dependent(int n)  
    {  
        int i;  
        int j;  
        if (n == 0)  
            i = 1;  
        else  
            j = 1;  
        return i+j;   
    }  
    ```  
  
9. Fare clic sul menu **File** e quindi fare clic su **Salva tutto**.  
  
### <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Aggiungere il progetto Annotations e configurarlo come libreria statica  
  
1. In Esplora soluzioni fare clic su **CppDemo**, scegliere **Aggiungi** e quindi fare clic su **Nuovo progetto**.  
  
2. Nella finestra di dialogo **Aggiungi nuovo progetto** espandere Visual C++, fare clic su **Generale** e quindi fare clic su **Progetto vuoto**.  
  
3. Nella casella di testo **Nome** digitare **Annotations** e quindi fare clic su **Aggiungi**.  
  
4. In Esplora soluzioni fare clic con il pulsante destro del mouse su **Annotations** e fare clic su **Proprietà**.  
  
5. Espandere **Proprietà di configurazione** e fare clic su **Generale**.  
  
6. Nell'elenco **Generale** selezionare il testo nella colonna accanto a **Estensione di destinazione** e digitare **.lib**.  
  
7. In **Impostazioni predefinite progetto** fare clic sulla colonna accanto a **Tipo configurazione** e quindi fare clic su **Libreria statica (.lib)** .  
  
### <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Aggiungere il file di intestazione e il file di origine per il progetto Annotations  
  
1. In Esplora soluzioni espandere **Annotations**, fare clic con il pulsante destro del mouse su **File di intestazione**, fare clic su **Aggiungi** e quindi fare clic su **Nuovo elemento**.  
  
2. Nella finestra di dialogo **Aggiungi nuovo elemento** fare clic su **File di intestazione (.h)** .  
  
3. Nella casella di testo **Nome** digitare **annotations.h** e quindi fare clic su **Aggiungi**.  
  
4. Copiare il codice seguente e incollarlo nella **Annotations. h** del file nei [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor.  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
  
    struct LinkedList  
    {  
        struct LinkedList* next;  
        int data;  
    };  
  
    typedef struct LinkedList LinkedList;  
  
    [returnvalue:SA_Post( Null=SA_Maybe )] LinkedList* AllocateNode();  
  
    ```  
  
5. In Esplora soluzioni fare clic con il pulsante destro del mouse su **File di origine**, scegliere **Nuovo** e quindi fare clic su **Nuovo elemento**.  
  
6. Nella finestra di dialogo **Aggiungi nuovo elemento** fare clic su **Codice** e quindi fare clic su **File di C++ (.cpp)** .  
  
7. Nella casella di testo **Nome** digitare **annotations.cpp** e quindi fare clic su **Aggiungi**.  
  
8. Copiare il codice seguente e incollarlo nella **Annotations. cpp** del file nei [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor.  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
    #include <windows.h>  
    #include <stdlib.h>    
    #include "annotations.h"  
  
    LinkedList* AddTail( LinkedList *node, int value )  
    {  
        LinkedList *newNode = NULL;   
  
        // finds the last node  
        while ( node->next != NULL )   
        {  
            node = node->next;  
        }  
  
        // appends the new node  
        newNode = AllocateNode();   
        newNode->data = value;  
        newNode->next = 0;  
        node->next = newNode;  
  
        return newNode;  
    }  
  
    ```  
  
9. Fare clic sul menu **File** e quindi fare clic su **Salva tutto**.

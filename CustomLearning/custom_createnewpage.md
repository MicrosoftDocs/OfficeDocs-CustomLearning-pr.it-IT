---
author: pkrebs
ms.author: pkrebs
title: Creare pagine di SharePoint per playlist
ms.date: 02/10/2019
description: Creare pagine di SharePoint per playlist
ms.openlocfilehash: c2de66a0746260e8f6539656ad70052b209c54ba
ms.sourcegitcommit: e10085e60ca3f38029fde229fb093e6bc4a34203
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "30103691"
---
# <a name="create-sharepoint-pages-for-custom-playlists"></a>Creare pagine di SharePoint per playlist personalizzate

Una delle caratteristiche esclusive dell'apprendimento personalizzato è la possibilità di creare playlist che vengono assemblate da risorse di Microsoft e da risorse di SharePoint create. In questo esempio viene creata una pagina di SharePoint prima della creazione di una playlist. La possibilità di creare playlist da pagine di SharePoint offre una vasta gamma di opportunità per creare pagine utilizzando le web part disponibili da Microsoft o dall'organizzazione. Ad esempio, una playlist può includere una pagina di SharePoint con video incorporati da YouTube o un modulo creato da moduli di Office 365 o un report incorporato di Power BI. In questo esempio viene illustrato come creare una pagina con la Web part embed e la Web part testo.  

## <a name="create-a-sharepoint-page-for-a-custom-playlist"></a>Creare una pagina di SharePoint per un elenco di riproduzione personalizzato

1. Fare clic sull' **** icona dell'ingranaGgio di SharePoint e quindi fare clic su **Aggiungi pagina**.
2. Fare clic su **Aggiungi una nuova sezione (+)** sul lato sinistro della pagina, quindi fare clic su **due colonne** per il layout della sezione.
3. Nella colonna sinistra fare clic su + e quindi fare clic sulla Web part **Embed** . 
4. Nella colonna a destra fare clic su +, quindi fare clic sulla Web part **testo** . La pagina dovrebbe essere simile alla seguente.

![CG-pagenewstart. png](media/cg-pagenewstart.png)

### <a name="add-a-video-and-text-from-youtube"></a>Aggiungere un video e un testo da YouTube

1. Nel browser Vai su YouTube. Per questo esempio, cercare "che cos'è Office 365 – le migliori app per la produttività di Microsoft".
2. Fare clic sul video per riprodurlo, quindi sospenderlo, quindi fare clic con il pulsante destro del mouse su di esso. 
3. Fare clic su **Copia codice embed**, quindi tornare alla pagina di SharePoint. 
4. Fare clic su **Aggiungi codice embed** nella web part **Embed** e quindi aggiungere il codice dal video di YouTube.
5. Tornare alla pagina di YouTube e copiare il testo della **Descrizione** del video. 
6. Tornare alla pagina di SharePoint, selezionare la Web part **testo** e quindi copiare il testo dal video di YouTube.
7. Selezionare l'icona **Modifica web part** nell'area del titolo della pagina di SharePoint e quindi denominare la pagina "introduzione di playlist personalizzate". 
8. Per **layout**, selezionare **pianura**, quindi riquadro delle proprietà dell' **area del titolo** . La pagina dovrebbe avere un aspetto analogo al seguente. 

![CG-pagenewfinish. png](media/cg-pagenewfinish.png)

### <a name="publish-the-page"></a>Pubblicare la pagina

- Selezionare il pulsante **pubblica** . A questo punto si è pronti per aggiungere questa pagina di SharePoint alla playlist personalizzata. 
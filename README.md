# Aluwani Madzhigili

I’m an accounts payable and bookkeeping professional based in Gauteng, South Africa. I have eight years of accounts payable experience, including supplier invoice processing, statement reconciliations, and bank reconciliations for four branches. I use QuickBooks and Excel and have completed training in prompt engineering.

I’m interested in AI training and response evaluation, especially tasks that require checking an answer against source documents and explaining corrections clearly. Connect with me on [LinkedIn](https://www.linkedin.com/in/aluwani-madzhigili-62376211a).

## Portfolio sample: AI invoice review

This worked example uses fictional records and an illustrative AI response to show how I would evaluate a model’s work.

### Source records

| Record | Quantity | Unit price | Line total before tax |
| --- | ---: | ---: | ---: |
| Purchase order PO-104 | 20 | R50.00 | R1,000.00 |
| Supplier invoice INV-208 | 20 | R55.00 | R1,100.00 |
| Goods receipt GR-104 | 20 received | — | — |

### Initial prompt and response

**Prompt:** Compare the purchase order, invoice, and goods receipt. Should the invoice proceed for payment review? Explain your answer.

**Illustrative response:** “Yes. The quantity of 20 matches across all documents and the invoice total is correct.”

### Evaluation

The quantity matches, and the invoice arithmetic is correct: 20 × R55 = R1,100. But the invoice unit price exceeds the purchase order by R5.00 per unit, or R100.00 before tax. The response treated a quantity match as sufficient and missed the price exception.

### Revised prompt

> Compare the purchase order, goods receipt, and supplier invoice line by line. Report quantity ordered, received, and invoiced, then compare ordered and invoiced unit prices. Recalculate the invoice line total and calculate the net variance as invoice line total minus purchase order line total. Cite the record IDs. If any quantity or price differs, return **Hold for human review** and explain the exception. Mark missing fields as unknown. Do not assume a variance tolerance or authorise payment.

**Expected response:** Hold for human review. The ordered, received, and invoiced quantities are all 20 (PO-104, GR-104, INV-208). INV-208 charges R55.00 per unit versus R50.00 on PO-104. The net variance is +R100.00 before tax. Ask the accounts payable team to confirm the approved price or request a corrected invoice.

### Review criteria

- Reports the 20-unit match across all three records.
- Flags the R5.00 unit-price difference and calculates the +R100.00 net variance.
- Cites the source record IDs and recommends a hold for human review.
- Avoids inventing a tax amount, tolerance, or payment approval.

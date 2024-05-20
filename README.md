# Pricing Structure
This document provides a comprehensive overview of the pricing structure associated with our API, including buses, trains, and ferries. It explains different pricing components, such as net and gross prices, and the variations of gross prices like maximum, minimum, exact, and recommended.
## Detailed Definitions of Pricing Components in API

#### Net Price
Net Price is the base cost of a service or product that is paid to the service provider or supplier. This price includes any direct costs associated with the service, such as operational costs, but excludes additional charges like markup, commissions, or other fees that may be added by intermediaries or resellers. It represents the fundamental cost of the primary service offered by the supplier.
Example of net price:

"net_price": {
    "currency": "USD",
    "amount": "75.00"  // This is the base amount paid to the supplier, excluding extras.
}
This indicates the amount that the transportation operator charges without any markup. It's the raw price that intermediaries base their final pricing upon.
#### Gross Price 
Gross Price in the TC API represents the limitation and describes the constraints around the gross price that the seller should apply. This is optional and appears when there is relevant data to share.
#### Variants of Gross Price
- **Max**: This is the maximum price that can be charged for a service. It sets an upper limit to ensure pricing strategies do not exceed what is contractually agreed with the suppliers.
- **Min**: The minimum price establishes a lower limit on the selling price. This practice is typically due to commercial agreements with suppliers, ensuring compliance with the terms set forth.
- **Exact**: An exact price is a specific price point that must be adhered to without deviation.
- **Recommended**: A recommended price serves as a guideline suggesting a price point that might be ideal based on market analysis, competitive pricing, or strategic objectives. It offers flexibility to adjust pricing based on real-time market conditions or competitive responses.

Example of Gross Price:

"gross_price": {
    "price_type": "Max",
    "amount": 15:00,
    "currency": "USD", // This indicates that there are contractual price restraints.
}
#### Taxes and Fees
**Taxes and Fees** are additional costs included in the net price that account for governmental taxes or operational fees which are necessary for the transaction. These are usually mandated by law or policy and vary by geographical location and type of service.

Example of Taxes and Fees:
"taxes_and_fees": {
    "currency": "USD",
    "amount": "5.00"
}
#### API Endpoint for Pricing Information
Pricing data can be retrieved via specific endpoints that provide details of itineraries, including the breakdown of net and gross prices.

Example API call:
{
    "itineraries": [
        {
            "id": "itinerary123",
            "departure_segments": [
                {
                    "id": "segment1234",
                    "departure_time": "2023-12-25T07:00:00",
                    "arrival_time": "2023-12-25T10:00:00",
                    "from_station": "123",
                    "to_station": "456"
                }
            ],
            "return_segments": [],
            "pricing": {
                "net_price": {
                    "currency": "USD",
                    "amount": "75.00"
                },
                "gross_price": {
                    "price_type": "recommended",
                    "currency": "USD",
                    "amount": "85.00",
                    "amount_in_net_currency": "75.00"
                },
                "taxes_and_fees": {
                    "currency": "USD",
                    "amount": "5.00"
                }
            },
            "confirmation_type": "Instant",
            "cancellation_policies": [
                {
                    "from": "P2D",
                    "penalty": {
                        "percentage": 50
                    }
                }
            ]
        }
    ]
}

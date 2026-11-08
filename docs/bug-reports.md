# API Testing – Bug Reports

While testing the Restful Booker API in Postman, I noticed a couple of issues with how the API handles incorrect or incomplete booking information.

The normal booking workflow worked as expected, but some of the negative test cases returned unexpected results.

## Bug 1: API Returns 500 When Required Fields Are Missing

**Endpoint:** `POST /booking`

**Description:**

I tested what would happen if I tried to create a booking without providing all the required information.

I sent the following request:

```json
{
  "totalprice": 250,
  "depositpaid": true
}
```

**Expected Result:**

I expected the API to reject the request with a validation error, such as HTTP 400 Bad Request, explaining that some required fields were missing.

**Actual Result:**

The API returned HTTP 500 Internal Server Error.

**Why this could be an issue:**

A 500 error usually suggests something went wrong on the server. Since the request was missing information, I would expect the API to handle it and return a more helpful error message.

**Status:** Potential bug – needs confirmation against the API requirements.

---

## Bug 2: API Accepts Invalid Data Types

**Endpoint:** `POST /booking`

**Description:**

I also wanted to see how the API would behave if I entered the wrong data types when creating a booking.

For this test, I used:

- `totalprice`: `"not-a-number"` instead of a number
- `depositpaid`: `"yes"` instead of a Boolean value

**Expected Result:**

I expected the API to reject the request with a validation error, such as HTTP 400 Bad Request, because the data types were incorrect.

**Actual Result:**

The API returned HTTP 200 OK and created a booking.

When I checked the response, I noticed that:

- `totalprice` had been changed to `null`.
- `depositpaid` had been changed to `true`.

**Why this could be an issue:**

The API accepted values that weren't in the expected format. This could lead to incorrect booking information being saved instead of letting the user know that the data needs to be corrected.

**Status:** Potential bug – needs confirmation against the API requirements.

---

## Summary

These two issues were found while carrying out negative API testing in Postman.

I kept the negative tests in a separate folder from my main CRUD workflow because some of the assertions fail when the API returns these unexpected results.

My main CRUD workflow still passes all 21 assertions when run through Postman, Newman, and GitHub Actions.

This testing helped me understand why negative testing is important. Even when the main API functionality works correctly, testing invalid inputs can reveal problems that might otherwise be missed.
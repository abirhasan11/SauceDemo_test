# Test Plan — Swag Labs (SauceDemo)

| | |
|---|---|
| **Project** | Manual test design for an e-commerce web application |
| **Application under test** | https://www.saucedemo.com (public demo store by Sauce Labs) |
| **Test type** | Manual — functional, negative and boundary |
| **Test artifacts** | `SauceDemo_Test_Design.xlsx` (RTM, TestCases, Coverage) |

---

## 1. Objective

Define what must be verified in the core shopping flow of the demo store — login, browsing, cart and checkout — and describe each check as a traceable, repeatable manual test case.

## 2. Scope

### In scope

| Area | Requirement | Test cases |
|---|---|:---:|
| Authentication | REQ-01 | 6 |
| Session & access control | REQ-02 | 2 |
| Product browsing & sorting | REQ-03 | 6 |
| Cart management | REQ-04 | 5 |
| Checkout | REQ-05 | 8 |
| Menu, logout & reset | REQ-06 | 2 |
| **Total** | | **29** |

### Out of scope

- Automation, API, performance, load and security penetration testing
- Payment gateway integration (the demo has no real payment)
- Mobile apps and cross-browser compatibility

## 3. Test Design Approach

| Technique | Where it is used |
|---|---|
| Requirement-based testing | Every test case traces back to a requirement in the RTM |
| Equivalence partitioning | Valid vs. invalid vs. empty credentials and form fields |
| Boundary value analysis | Case-sensitive username, 250-character and special-character postal code |
| Error guessing | Direct URL access, back button after logout, empty-cart checkout |
| Behaviour comparison | `problem_user` against the baseline `standard_user` |

## 4. Test Environment (target)

| Item | Value |
|---|---|
| Browser | Google Chrome (latest) |
| Test accounts | `standard_user`, `locked_out_user`, `problem_user` (password shown on the login page) |
| Test data | Included in each test case |

## 5. Entry & Exit Criteria

**Entry**
- The application is reachable in the browser.
- Requirements are written and reviewed.

**Exit (design phase)**
- Every requirement has at least one scenario and one test case in the RTM.
- Every test case has preconditions, test data, steps and an expected result.
- Positive, negative and boundary conditions are covered.

## 6. Defect Classification (reference for the execution phase)

| Severity | Meaning |
|---|---|
| Critical | Core flow is blocked or data is lost, no workaround |
| High | Major function is broken, workaround is difficult |
| Medium | Function misbehaves but a workaround exists |
| Low | Cosmetic or minor inconvenience |

| Priority | Meaning |
|---|---|
| High | Fix first — affects many users or a key flow |
| Medium | Fix in the normal course of work |
| Low | Fix when time allows |

**Lifecycle:** `Open → In Progress → Fixed → Retest → Closed` (or `Reopened` if the original issue still reproduces). A different issue found during retest is logged as a new linked defect.

## 7. Deliverables

| Deliverable | Location |
|---|---|
| Test plan | `docs/Test_Plan.md` |
| RTM, scenarios, test cases, coverage summary | `SauceDemo_Test_Design.xlsx` |

## 8. Risks & Assumptions

| Risk / assumption | Note |
|---|---|
| The demo site can change without notice | Expected results reflect the documented behaviour of the site at design time |
| Some accounts (`problem_user`) are built to misbehave | Their test cases compare behaviour against `standard_user` |

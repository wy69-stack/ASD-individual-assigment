
This document outlines the user stories and acceptance criteria for the PawBuddy Minimum Viable Product (MVP).

---

## 1. Feature: Look for Nearby Pet Care Providers

### US-01: View Nearby Caregivers
* **As a** pet owner,
* **I want to** search and view pet sitters, dog walkers, and boarding services around my location,
* **So that** I can easily find accessible care options for my pet.

#### Scenario 1: Displaying Nearby Providers
* **Given** the pet owner opens the PawBuddy search page,
* **When** they enter their location or select an area,
* **Then** the system displays a list of active pet care providers operating in or near that location.

#### Scenario 2: No Providers Found
* **Given** the pet owner searches for a location with no registered providers,
* **When** the query executes,
* **Then** the system displays a clear message stating "No pet care providers found in this area."

---

## 2. Feature: Select Pet Care Service

### US-02: Filter by Service Category
* **As a** pet owner,
* **I want to** choose a specific pet care service (e.g., pet sitting, dog walking, pet boarding),
* **So that** I only see providers who offer the exact service my pet needs.

#### Scenario 1: Filtering Providers by Service Type
* **Given** the search page shows all nearby providers,
* **When** the pet owner selects "Dog Walking" from the service options,
* **Then** the result list updates to display only providers who offer dog walking services.

---

## 3. Feature: View Provider Information

### US-03: Provider Profile Details
* **As a** pet owner,
* **I want to** view a provider's profile details including experience, price, location, and services,
* **So that** I can determine if they are trustworthy and suited for my pet.

#### Scenario 1: Opening a Caregiver Profile
* **Given** the search results list,
* **When** the pet owner clicks on a specific provider's name or profile card,
* **Then** the system opens the full profile page showing their photo, experience, hourly/daily rate, location area, and offered services.

---

## 4. Feature: Book a Service

### US-04: Submit a Booking Request
* **As a** pet owner,
* **I want to** select a provider, choose a date and time, and send a booking request,
* **So that** I can reserve pet care for my upcoming schedule.

#### Scenario 1: Successful Booking Request
* **Given** the pet owner is on a selected provider's profile page,
* **When** they select a valid date, choose start/end times, and click "Send Booking Request",
* **Then** the system creates a new booking entry with status `Pending`,
* **And** displays a confirmation message with the booking summary.

#### Scenario 2: Submitting Incomplete Booking Details
* **Given** the booking modal on a provider's profile,
* **When** the pet owner clicks "Send Booking Request" without choosing a date or time,
* **Then** the system prevents submission and highlights the missing fields in red.
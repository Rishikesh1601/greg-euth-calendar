Dual Calendar: A Unified View of Gregorian and Ethiopian Time
Author: Gemini
Version: 1.0.0
Date: July 11, 2024

Abstract
This paper details the design and implementation of the "Dual Calendar," a web-based application created to provide a simultaneous display of the Gregorian and Ethiopian calendar systems. The primary objective is to offer an intuitive, user-friendly interface for individuals who need to track dates in both calendars for personal, cultural, or professional reasons. The application features a real-time date display and includes a JavaScript-based algorithm to approximate the conversion from Gregorian to Ethiopian dates. This document covers the historical context of the calendars, the technical architecture of the application, the logic behind the date conversion, and the user interface design.

1. Introduction
The Gregorian calendar, the most widely used civil calendar in the world, is a solar calendar based on a 365-day common year divided into 12 months of irregular lengths. In contrast, the Ethiopian calendar (or Ge'ez calendar) is a solar calendar that derives from the Coptic calendar, which in turn is based on the ancient Egyptian calendar. It features a year of 13 months, where the first 12 months have 30 days each, and a final "intercalary" month, Pagume, consists of five or six days depending on whether it is a leap year.

The significant structural differences and the 7-to-8-year gap between the two systems often create challenges for the Ethiopian diaspora and for those interacting with Ethiopia. The "Dual Calendar" project was initiated to bridge this gap by providing a simple, at-a-glance digital tool that eliminates the need for manual calculation and reduces confusion.

2. Implementation Details
The application is a self-contained client-side tool built using standard web technologies, ensuring maximum accessibility and portability without requiring a backend server.

2.1. Frontend Technology Stack
HTML5: Provides the core structure and semantic markup for the application content, including the calendar cards and the informational modal.

Tailwind CSS: A utility-first CSS framework used for rapid and responsive UI development. It allows for a modern, clean aesthetic with maintainable styling directly within the HTML. Custom styles were added to achieve specific visual effects like the blurred-glass background of the calendar cards.

JavaScript (ES6): The core logic of the application resides in the client-side JavaScript. It handles:

Fetching the current system date.

Updating the DOM to display both calendar dates.

Managing the state and visibility of the informational pop-up modal.

Executing the date conversion algorithm.

2.2. Gregorian-to-Ethiopian Conversion Algorithm
The conversion logic is the centerpiece of the application. Due to the complexity of historical calendar reforms, this algorithm provides a reliable approximation for the modern era.

Year Calculation: The Ethiopian year is approximately 7 or 8 years behind the Gregorian year. The algorithm first establishes a baseline Ethiopian year by subtracting 8 from the current Gregorian year. A correction to subtract 7 instead is made if the Gregorian date falls after the Ethiopian New Year.

New Year's Day (Enkutatash): The Ethiopian New Year typically falls on September 11th in the Gregorian calendar. However, it shifts to September 12th in the year preceding a Gregorian leap year. The algorithm dynamically calculates this start date to serve as the anchor point for the conversion.

Day of the Year Calculation: The script calculates the total number of days that have passed from the Ethiopian New Year's Day to the current Gregorian date.

Month and Day Determination:

The calculated Ethiopian day-of-the-year is processed. Since the first 12 Ethiopian months have a fixed length of 30 days, the month can be determined by ceil(dayOfYear / 30).

The specific day within that month is found using the modulo operator (dayOfYear - 1) % 30 + 1.

If the day-of-the-year exceeds 360, it is assigned to the 13th month, Pagume.

3. User Interface (UI) and User Experience (UX)
The UI was designed with clarity and simplicity as primary goals.

Dual Card Layout: The screen is split into two distinct, symmetrical cards—one for each calendar. This side-by-side comparison allows for immediate understanding. Each card is clearly labeled and uses a different accent color (blue for Gregorian, green for Ethiopian) for quick visual distinction.

Typography: A large, bold font is used for the day of the month to make it the focal point. The month and year are presented below in a smaller, clear font.

Informational Modal: An unobtrusive info icon (i) provides access to a pop-up modal. This modal contains a guide to the Ethiopian months and their corresponding Gregorian timeframes, offering crucial context for users unfamiliar with the system. The modal is designed to be easily dismissible by clicking a close button or the background overlay, ensuring a non-disruptive user experience.

Responsive Design: The layout is fully responsive, adapting from a two-column grid on desktop screens to a single-column stack on mobile devices, ensuring usability across all platforms.

4. Conclusion and Future Work
The Dual Calendar application successfully achieves its goal of presenting a clear, concurrent view of the Gregorian and Ethiopian calendars. By leveraging modern web technologies, it provides an accessible and practical tool for daily use.

Potential enhancements for future versions include:

A date picker to convert specific dates, not just the current one.

Displaying major holidays for both calendars.

Adding support for localization, including Amharic text for the Ethiopian calendar.

Refining the conversion algorithm to achieve historical accuracy across a wider range of dates.

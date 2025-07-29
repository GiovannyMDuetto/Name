# Name

description

```
when the user clicks here, open this Data Picker as a floating div and make sure the range choosed on the data picker will be the range showed here when the user clicks apply.

import { useState } from "react";
import { defineProperties } from "figma:react";
import svgPaths from "./svg-yq6amhk3b5";
// Tailwind's scrollbar-thin utility will render a small native scrollbar in supported browsers

interface DatePickerMonthNavButtonProps {
  icon?: React.ReactNode | null;
  hoverState?: "false" | "true";
  onClick?: () => void;
  className?: string;
}

function DatePickerMonthNavButton({
  icon = null,
  hoverState = "false",
  onClick,
  className = "",
}: DatePickerMonthNavButtonProps) {
  if (hoverState === "true") {
    return (
      <div
        className={`bg-neutral-100 box-border content-stretch flex flex-row items-center justify-start p-0 relative rounded-xl size-full cursor-pointer ${className}`}
        data-name="Hover state=true"
        onClick={onClick}
      >
        <div
          className="overflow-clip relative shrink-0 size-6"
          data-name="chevron_left"
        >
          <div
            className="absolute bottom-1/4 left-[34.563%] right-[34.563%] top-1/4"
            data-name="Vector"
          >
            <svg
              className="block size-full"
              fill="none"
              preserveAspectRatio="none"
              role="presentation"
              viewBox="0 0 8 12"
            >
              <g id="Vector">
                <path d={svgPaths.p10001380} fill="var(--fill-0, #585858)" />
              </g>
            </svg>
          </div>
        </div>
      </div>
    );
  }
  return (
    <div
      className={`box-border content-stretch flex flex-row items-center justify-start p-0 relative rounded-xl size-full cursor-pointer ${className}`}
      data-name="Hover state=false"
      onClick={onClick}
    >
      {icon || (
        <div
          className="overflow-clip relative shrink-0 size-6"
          data-name="chevron_left"
        >
          <div
            className="absolute bottom-1/4 left-[34.563%] right-[34.563%] top-1/4"
            data-name="Vector"
          >
            <svg
              className="block size-full"
              fill="none"
              preserveAspectRatio="none"
              role="presentation"
              viewBox="0 0 8 12"
            >
              <g id="Vector">
                <path d={svgPaths.p10001380} fill="var(--fill-0, #585858)" />
              </g>
            </svg>
          </div>
        </div>
      )}
    </div>
  );
}

function MenuDivider() {
  return (
    <div
      className="box-border content-stretch flex flex-col gap-2 items-start justify-start p-0 relative size-full"
      data-name="Menu/Divider"
    >
      <div className="bg-[#e0e0e0] h-px shrink-0 w-full" />
    </div>
  );
}

function Spacer() {
  return <div className="shrink-0 size-6" data-name="spacer" />;
}

function DatePickerMonthNav() {
  return (
    <div
      className="box-border content-stretch flex flex-row gap-1 h-6 items-center justify-start p-0 relative shrink-0 w-full"
      data-name="date-picker-month-nav"
    >
      <div
        className="box-border content-stretch flex flex-row items-center justify-start p-0 relative rounded-xl shrink-0"
        data-name="go back two months"
      >
        <div
          className="overflow-clip relative shrink-0 size-6"
          data-name="Style=Outlined"
        >
          <div
            className="absolute bottom-1/4 left-[20.833%] right-[20.833%] top-1/4"
            data-name="Vector"
          >
            <svg
              className="block size-full"
              fill="none"
              preserveAspectRatio="none"
              role="presentation"
              viewBox="0 0 14 12"
            >
              <g id="Vector">
                <path d={svgPaths.p8039dc0} fill="var(--fill-0, #585858)" />
                <path d={svgPaths.p67fcb00} fill="var(--fill-0, #585858)" />
              </g>
            </svg>
          </div>
        </div>
      </div>
      <div
        className="box-border content-stretch flex flex-row items-center justify-start p-0 relative rounded-xl shrink-0"
        data-name="go back one month"
      >
        <DatePickerMonthNavButton />
      </div>
      <div className="basis-0 flex flex-col font-['Lato:Bold',_sans-serif] grow justify-center leading-[0] min-h-px min-w-px not-italic relative shrink-0 text-[#1c1c1c] text-[16px] text-center">
        <p className="block leading-[normal]">July 2025</p>
      </div>
      {[...Array(2).keys()].map((_, i) => (
        <Spacer key={i} />
      ))}
    </div>
  );
}

function DatePickerWeekLegend() {
  return (
    <div
      className="box-border content-stretch flex flex-row font-['Lato:Regular',_sans-serif] items-center justify-start leading-[0] not-italic px-0 py-2 relative shrink-0 text-[#585858] text-[16px] text-center w-full"
      data-name="date-picker-week-legend"
    >
      {["Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"].map((day, index) => (
        <div key={index} className="flex flex-col justify-center relative shrink-0 w-10">
          <p className="block leading-[normal]">{day}</p>
        </div>
      ))}
    </div>
  );
}

function Spacer2() {
  return <div className="rounded-[20px] shrink-0 size-10" data-name="spacer" />;
}

interface DatePickerDayProps {
  day: number;
  month: string;
  onClick: () => void;
  isSelected: boolean;
  isRangeStart: boolean;
  isRangeEnd: boolean;
  isInRange: boolean;
  onHover: () => void;
  hoverDate: { day: number; month: string } | null;
  startDate: { day: number; month: string } | null;
  endDate: { day: number; month: string } | null;
  isHovered: boolean;
}

function DatePickerDay({
  day,
  month,
  onClick,
  isSelected,
  isRangeStart,
  isRangeEnd,
  isInRange,
  onHover,
  hoverDate,
  startDate,
  endDate,
  isHovered
}: DatePickerDayProps) {
  let textClass = "text-[#585858]";
  
  // Text color logic
  if (isSelected || isRangeStart || isRangeEnd || isInRange) {
    textClass = "text-[#FFFFFF]";
  }
  
  // Determine if this day is the start/end of hover selection
  const isHoverSelectionStart = startDate && !endDate && hoverDate && 
    ((startDate.day === day && startDate.month === month && 
      ((startDate.month === hoverDate.month && startDate.day > hoverDate.day) || 
       (startDate.month > hoverDate.month))) ||
     (hoverDate.day === day && hoverDate.month === month && 
      ((startDate.month === hoverDate.month && startDate.day > hoverDate.day) || 
       (startDate.month > hoverDate.month))));
  
  const isHoverSelectionEnd = startDate && !endDate && hoverDate && 
    ((startDate.day === day && startDate.month === month && 
      ((startDate.month === hoverDate.month && startDate.day < hoverDate.day) || 
       (startDate.month < hoverDate.month))) ||
     (hoverDate.day === day && hoverDate.month === month && 
      ((startDate.month === hoverDate.month && startDate.day < hoverDate.day) || 
       (startDate.month < hoverDate.month))));
  
  const isHoverSelectionMiddle = startDate && !endDate && hoverDate && 
    !isHoverSelectionStart && !isHoverSelectionEnd && 
    ((startDate.month === hoverDate.month && month === startDate.month && 
      day > Math.min(startDate.day, hoverDate.day) && day < Math.max(startDate.day, hoverDate.day)) ||
     (startDate.month !== hoverDate.month && 
      ((month === startDate.month && startDate.month < hoverDate.month && day > startDate.day) || 
       (month === startDate.month && startDate.month > hoverDate.month && day < startDate.day) ||
       (month === hoverDate.month && startDate.month < hoverDate.month && day < hoverDate.day) ||
       (month === hoverDate.month && startDate.month > hoverDate.month && day > hoverDate.day) ||
       (month > startDate.month && month < hoverDate.month) ||
       (month < startDate.month && month > hoverDate.month))));
  
  return (
    <div
      className="size-10 relative shrink-0 cursor-pointer flex items-center justify-center"
      data-name={`.date-picker-day${day < 10 ? '0' : ''}${day}`}
      onClick={onClick}
      onMouseEnter={onHover}
    >
      {/* Background shape layer - This is the layer that controls the visual shape */}
      {(isSelected || isRangeStart || isRangeEnd || isInRange || isHovered || 
        isHoverSelectionStart || isHoverSelectionEnd || isHoverSelectionMiddle) && (
        <div 
          className={`absolute inset-0 z-0 bg-[#2D64E8] ${
            // Single day selection or hover - fully rounded
            (isSelected && !isRangeStart && !isRangeEnd) || 
            (isHovered && !startDate) || 
            (startDate && !endDate && isHovered && startDate.day === day && startDate.month === month)
              ? "rounded-[20px]" 
            // Range start or hover selection start - left rounded only
            : (isRangeStart || isHoverSelectionStart) 
              ? "rounded-l-[20px]" 
            // Range end or hover selection end - right rounded only
            : (isRangeEnd || isHoverSelectionEnd) 
              ? "rounded-r-[20px]" 
            // Middle days - no rounding
            : ""
          }`}
        />
      )}
      
      {/* Black overlay for selected range endpoints */}
      {(isRangeStart || isRangeEnd || isHoverSelectionStart || isHoverSelectionEnd) && (
        <div className="absolute inset-0 z-10 bg-black opacity-10 rounded-[20px]" />
      )}
      
      {/* Date text - always on top */}
      <div className={`z-20 flex flex-col font-['Lato:Regular',_sans-serif] justify-center leading-[0] not-italic relative shrink-0 ${textClass} text-[16px] text-center`}>
        <p className="block leading-[normal]">{day}</p>
      </div>
    </div>
  );
}

function ActionsBar({ startDate, endDate, onApply, onCancel }) {
  const formatDateString = (date) => {
    if (!date) return "";
    return `${date.month} ${date.day}, 2025`;
  };
  
  let dateRangeText = "-";
  if (startDate) {
    if (endDate) {
      dateRangeText = `${formatDateString(startDate)} - ${formatDateString(endDate)}`;
    } else {
      dateRangeText = formatDateString(startDate);
    }
  }
  
  return (
    <div
      className="box-border content-stretch flex flex-row gap-4 items-center justify-end pb-0 pt-4 px-0 relative shrink-0 w-full"
      data-name="actions-bar"
    >
      <div className="absolute border-[#e0e0e0] border-[1px_0px_0px] border-solid inset-0 pointer-events-none" />
      <div className="basis-0 flex flex-col font-['Lato:Regular',_sans-serif] grow justify-center leading-[0] min-h-px min-w-px not-italic relative shrink-0 text-[#1c1c1c] text-[14px] text-left">
        <p className="block leading-[normal]">{dateRangeText}</p>
      </div>
      <div
        className="box-border content-stretch flex flex-row gap-2 h-9 items-center justify-center px-4 py-2 relative rounded shrink-0 cursor-pointer"
        data-name="cancel Button"
        onClick={onCancel}
      >
        <div className="flex flex-col font-['Lato:Regular',_sans-serif] justify-center leading-[0] not-italic relative shrink-0 text-[#1b4dc0] text-[14px] text-left text-nowrap">
          <p className="block leading-[normal] whitespace-pre">Cancel</p>
        </div>
      </div>
      <div
        className="bg-[#1b4dc0] box-border content-stretch flex flex-row gap-2 h-9 items-center justify-center px-4 py-2 relative rounded shrink-0 cursor-pointer"
        data-name="apply Button"
        onClick={onApply}
      >
        <div className="flex flex-col font-['Lato:Regular',_sans-serif] justify-center leading-[0] not-italic relative shrink-0 text-[#ffffff] text-[14px] text-left text-nowrap">
          <p className="block leading-[normal] whitespace-pre">Apply</p>
        </div>
      </div>
    </div>
  );
}

function TodayButton() {
  return (
    <div
      className="box-border content-stretch flex flex-row gap-2.5 items-center justify-center p-[8px] relative rounded-[20px] shrink-0 cursor-pointer"
      data-name="today button"
    >
      <div className="flex flex-col font-['Lato:Regular',_sans-serif] justify-center leading-[0] not-italic relative shrink-0 text-[#1b4dc0] text-[16px] text-left text-nowrap">
        <p className="block leading-[normal] whitespace-pre">Today</p>
      </div>
    </div>
  );
}

function TomorrowBar() {
  return (
    <div
      className="box-border content-stretch flex flex-row gap-2.5 items-center justify-center p-[8px] relative rounded-[20px] shrink-0 cursor-pointer"
      data-name="tomorrow bar"
    >
      <div className="flex flex-col font-['Lato:Regular',_sans-serif] justify-center leading-[0] not-italic relative shrink-0 text-[#1b4dc0] text-[16px] text-left text-nowrap">
        <p className="block leading-[normal] whitespace-pre">Tomorrow</p>
      </div>
    </div>
  );
}

function Divider() {
  return (
    <div
      className="box-border content-stretch flex flex-col gap-2.5 items-start justify-start px-0 py-4 relative shrink-0 w-full"
      data-name="divider"
    >
      <div
        className="box-border content-stretch flex flex-col gap-2 items-start justify-start p-0 relative shrink-0 w-full"
        data-name="Menu/Divider"
      >
        <MenuDivider />
      </div>
    </div>
  );
}

function Title({ title }) {
  return (
    <div
      className="box-border content-stretch flex flex-row gap-2.5 items-center justify-start px-0 py-2 relative shrink-0 w-full"
      data-name="title"
    >
      <div className="basis-0 flex flex-col font-['Lato:Bold',_sans-serif] grow justify-center leading-[0] min-h-px min-w-px not-italic relative shrink-0 text-[#585858] text-[16px] text-left">
        <p className="block leading-[normal]">{title}</p>
      </div>
    </div>
  );
}

function SidebarButton({ label, isActive = false, onClick }) {
  return (
    <div
      className={`box-border content-stretch flex flex-row gap-2.5 items-center justify-center p-[8px] relative rounded-[20px] shrink-0 cursor-pointer ${isActive ? 'bg-[#2d64e8]' : ''}`}
      data-name={`${label} button`}
      onClick={onClick}
    >
      <div className={`flex flex-col font-['Lato:Regular',_sans-serif] justify-center leading-[0] not-italic relative shrink-0 ${isActive ? 'text-[#ffffff]' : 'text-[#1b4dc0]'} text-[16px] text-left text-nowrap`}>
        <p className="block leading-[normal] whitespace-pre">{label}</p>
      </div>
    </div>
  );
}

function SideBarScroll({ activeButton, onButtonClick }) {
  return (
    <div
      className="basis-0 box-border content-stretch flex flex-col grow h-full items-start justify-start min-h-px min-w-px p-0 relative shrink-0 overflow-y-auto scrollbar-thin pr-2"
      data-name="side bar - scroll"
    >
      <TodayButton />
      <TomorrowBar />
      <Divider />
      <Title title="Current" />
      <SidebarButton label="Week" isActive={activeButton === "Week"} onClick={() => onButtonClick("Week")} />
      <SidebarButton label="Month" isActive={activeButton === "Month"} onClick={() => onButtonClick("Month")} />
      <Divider />
      <Title title="Next" />
      <SidebarButton label="7 Days" isActive={activeButton === "7 Days"} onClick={() => onButtonClick("7 Days")} />
      <SidebarButton label="14 Days" isActive={activeButton === "14 Days"} onClick={() => onButtonClick("14 Days")} />
      <SidebarButton label="30 Days" isActive={activeButton === "30 Days"} onClick={() => onButtonClick("30 Days")} />
      <SidebarButton label="90 Days" isActive={activeButton === "90 Days"} onClick={() => onButtonClick("90 Days")} />
      <SidebarButton label="180 Days" isActive={activeButton === "180 Days"} onClick={() => onButtonClick("180 Days")} />
      <SidebarButton label="365 Days" isActive={activeButton === "365 Days"} onClick={() => onButtonClick("365 Days")} />
    </div>
  );
}

function Frame1101({ activeButton, onButtonClick }) {
  return (
    <div className="relative self-stretch shrink-0 w-fit max-w-[160px]">
      <div className="box-border content-stretch flex flex-row h-full items-start justify-start overflow-hidden pl-4 pr-0 py-0 relative w-full">
        <SideBarScroll activeButton={activeButton} onButtonClick={onButtonClick} />
      </div>
      <div className="absolute border-[#e0e0e0] border-l border-solid inset-0 pointer-events-none" />
    </div>
  );
}

// Utility functions for date manipulation
const MONTHS = [
  "January", "February", "March", "April", "May", "June",
  "July", "August", "September", "October", "November", "December"
];

// Function to generate calendar data for a specific month and year
function generateCalendarData(month, year) {
  const firstDay = new Date(year, month, 1).getDay(); // 0 = Sunday, 1 = Monday, etc.
  const daysInMonth = new Date(year, month + 1, 0).getDate();
  
  let calendar = [];
  let week = Array(7).fill(null);
  
  // Fill in the first week with null for days before the first of the month
  for (let i = firstDay; i < 7; i++) {
    week[i] = i - firstDay + 1;
  }
  calendar.push(week);
  
  // Fill in the rest of the weeks
  let day = 7 - firstDay + 1;
  while (day <= daysInMonth) {
    week = Array(7).fill(null);
    for (let i = 0; i < 7 && day <= daysInMonth; i++) {
      week[i] = day++;
    }
    calendar.push(week);
  }
  
  return calendar;
}

function Month({ 
  displayMonth,
  displayYear,
  startDate, 
  endDate,
  onDayClick,
  hoverDate,
  onDayHover,
  onNavigateMonth,
  isFirstMonth // Added parameter to determine if it's the first month
}) {
  const monthKey = `${displayMonth}-${displayYear}`;
  const monthTitle = `${MONTHS[displayMonth]} ${displayYear}`;
  
  // Generate calendar data for this month
  const calendarData = generateCalendarData(displayMonth, displayYear);
  
  // Determine if a day is in the selected range
  const isDayInRange = (day, monthKey) => {
    if (!startDate || !endDate || !day) return false;
    
    const currentMonthYear = monthKey.split("-");
    const currentMonth = parseInt(currentMonthYear[0]);
    const currentYear = parseInt(currentMonthYear[1]);
    
    const currentDate = new Date(currentYear, currentMonth, day);
    const start = new Date(startDate.year, startDate.month, startDate.day);
    const end = new Date(endDate.year, endDate.month, endDate.day);
    
    return currentDate >= start && currentDate <= end;
  };
  
  // Determine if day is in the hover range (when selecting)
  const isDayInHoverRange = (day, monthKey) => {
    if (!startDate || !hoverDate || endDate || !day) return false;
    
    const currentMonthYear = monthKey.split("-");
    const currentMonth = parseInt(currentMonthYear[0]);
    const currentYear = parseInt(currentMonthYear[1]);
    
    const currentDate = new Date(currentYear, currentMonth, day);
    const start = new Date(startDate.year, startDate.month, startDate.day);
    const hover = new Date(hoverDate.year, hoverDate.month, hoverDate.day);
    
    return (currentDate >= start && currentDate <= hover) ||
           (currentDate >= hover && currentDate <= start);
  };

  // Helper function to get full month name
  const getMonthName = (month) => MONTHS[month];
  
  return (
    <div
      className="box-border content-stretch flex flex-col gap-4 items-start justify-start p-0 relative shrink-0 w-[280px]"
      data-name="month-with-navigation"
    >
      <div
        className="box-border content-stretch flex flex-row gap-1 h-6 items-center justify-start p-0 relative shrink-0 w-full"
        data-name="date-picker-month-nav"
      >
        {isFirstMonth ? (
          // Only show back navigation buttons for the first month
          <>
            <div
              className="box-border content-stretch flex flex-row items-center justify-start p-0 relative rounded-xl shrink-0 cursor-pointer"
              data-name="go back one year"
              onClick={() => onNavigateMonth('prev-year')}
            >
              <div
                className="overflow-clip relative shrink-0 size-6"
                data-name="Style=Outlined"
              >
                <div
                  className="absolute bottom-1/4 left-[20.833%] right-[20.833%] top-1/4"
                  data-name="Vector"
                >
                  <svg
                    className="block size-full"
                    fill="none"
                    preserveAspectRatio="none"
                    role="presentation"
                    viewBox="0 0 14 12"
                  >
                    <g id="Vector">
                      <path d={svgPaths.p8039dc0} fill="var(--fill-0, #585858)" />
                      <path d={svgPaths.p67fcb00} fill="var(--fill-0, #585858)" />
                    </g>
                  </svg>
                </div>
              </div>
            </div>
            <div
              className="box-border content-stretch flex flex-row items-center justify-start p-0 relative rounded-xl shrink-0 cursor-pointer"
              data-name="go back one month"
              onClick={() => onNavigateMonth('prev')}
            >
              <DatePickerMonthNavButton />
            </div>
          </>
        ) : null}
        
        {/* Month title is always shown */}
        <div className="basis-0 flex flex-col font-['Lato:Bold',_sans-serif] grow justify-center leading-[0] min-h-px min-w-px not-italic relative shrink-0 text-[#1c1c1c] text-[16px] text-center">
          <p className="block leading-[normal]">{monthTitle}</p>
        </div>
        
        {isFirstMonth ? (
          // Nothing on the right side for the first month now
          <></>
        ) : (
          // Show the forward month and forward year buttons on the second month
          <>
            <div
              className="box-border content-stretch flex flex-row items-center justify-start p-0 relative rounded-xl shrink-0 cursor-pointer"
              data-name="go forward one month"
              onClick={() => onNavigateMonth('next')}
            >
              <div
                className="overflow-clip relative shrink-0 size-6"
                data-name="Style=Outlined"
              >
                <div
                  className="absolute bottom-1/4 left-[34.563%] right-[34.563%] top-1/4"
                  data-name="Vector"
                >
                  <svg
                    className="block size-full"
                    fill="none"
                    preserveAspectRatio="none"
                    role="presentation"
                    viewBox="0 0 8 12"
                  >
                    <g id="Vector">
                      <path d={svgPaths.p25284240} fill="var(--fill-0, #585858)" />
                    </g>
                  </svg>
                </div>
              </div>
            </div>
            <div
              className="box-border content-stretch flex flex-row items-center justify-start p-0 relative rounded-xl shrink-0 cursor-pointer"
              data-name="go forward one year"
              onClick={() => onNavigateMonth('next-year')}
            >
              <div
                className="overflow-clip relative shrink-0 size-6"
                data-name="Style=Outlined"
              >
                <div
                  className="absolute bottom-1/4 left-[20.833%] right-[20.833%] top-1/4"
                  data-name="Vector"
                >
                  <svg
                    className="block size-full"
                    fill="none"
                    preserveAspectRatio="none"
                    role="presentation"
                    viewBox="0 0 14 12"
                  >
                    <g id="Vector">
                      <path d={svgPaths.p25284240} fill="var(--fill-0, #585858)" />
                      <path d={svgPaths.p2d18c680} fill="var(--fill-0, #585858)" />
                    </g>
                  </svg>
                </div>
              </div>
            </div>
          </>
        )}
      </div>
      
      <div
        className="box-border content-stretch flex flex-col items-start justify-start p-0 relative shrink-0 w-full"
        data-name="date-picker-month"
      >
        <DatePickerWeekLegend />
        
        {calendarData.map((week, weekIndex) => (
          <div
            key={weekIndex}
            className="box-border content-stretch flex flex-row items-center justify-start p-0 relative shrink-0"
            data-name=".date-picker-week"
          >
            {week.map((day, dayIndex) => {
              if (day === null) {
                return <Spacer2 key={dayIndex} />;
              }
              
              const currentMonthYear = `${displayMonth}-${displayYear}`;
              const isStartDate = startDate && 
                startDate.day === day && 
                startDate.month === displayMonth && 
                startDate.year === displayYear;
              
              const isEndDate = endDate && 
                endDate.day === day && 
                endDate.month === displayMonth && 
                endDate.year === displayYear;
              
              const inRange = isDayInRange(day, currentMonthYear) || isDayInHoverRange(day, currentMonthYear);
              const inRangeButNotEndpoint = inRange && !isStartDate && !isEndDate;
              
              const isHovered = hoverDate && 
                hoverDate.day === day && 
                hoverDate.month === displayMonth && 
                hoverDate.year === displayYear;
              
              return (
                <DatePickerDay
                  key={dayIndex}
                  day={day}
                  month={currentMonthYear}
                  onClick={() => onDayClick(day, displayMonth, displayYear)}
                  isSelected={isStartDate || isEndDate}
                  isRangeStart={isStartDate && endDate !== null && (
                    startDate.day !== endDate.day || 
                    startDate.month !== endDate.month || 
                    startDate.year !== endDate.year
                  )}
                  isRangeEnd={isEndDate && startDate !== null && (
                    startDate.day !== endDate.day || 
                    startDate.month !== endDate.month || 
                    startDate.year !== endDate.year
                  )}
                  isInRange={inRangeButNotEndpoint}
                  onHover={() => onDayHover(day, displayMonth, displayYear)}
                  hoverDate={hoverDate}
                  startDate={startDate}
                  endDate={endDate}
                  isHovered={isHovered}
                />
              );
            })}
          </div>
        ))}
      </div>
    </div>
  );
}

export default function DatePickerCalendar() {
  // Get current date to initialize with
  const today = new Date();
  const currentMonth = today.getMonth(); // 0-11
  const currentYear = today.getFullYear();
  
  // State for month navigation
  const [displayMonths, setDisplayMonths] = useState([
    { month: currentMonth, year: currentYear },
    { month: (currentMonth + 1) % 12, year: currentMonth === 11 ? currentYear + 1 : currentYear }
  ]);
  
  // State for date selection
  const [startDate, setStartDate] = useState(null);
  const [endDate, setEndDate] = useState(null);
  const [hoverDate, setHoverDate] = useState(null);
  const [activeButton, setActiveButton] = useState("7 Days");
  
  // Handle month navigation - now always modifies both months together
  const handleMonthNavigation = (direction) => {
    setDisplayMonths(prevMonths => {
      // First month in the pair
      let { month, year } = prevMonths[0];
      
      switch(direction) {
        case 'prev':
          month = month - 1;
          if (month < 0) {
            month = 11;
            year -= 1;
          }
          break;
        case 'next':
          month = month + 1;
          if (month > 11) {
            month = 0;
            year += 1;
          }
          break;
        case 'prev-year':
          year -= 1;
          break;
        case 'next-year':
          year += 1;
          break;
      }
      
      // Calculate second month which is always one month ahead
      let nextMonth = month + 1;
      let nextYear = year;
      if (nextMonth > 11) {
        nextMonth = 0;
        nextYear += 1;
      }
      
      return [
        { month, year },
        { month: nextMonth, year: nextYear }
      ];
    });
  };
  
  const handleDayClick = (day, month, year) => {
    if (!startDate || (startDate && endDate)) {
      // Start new selection
      setStartDate({ day, month, year });
      setEndDate(null);
    } else {
      // Complete the selection
      const newEndDate = { day, month, year };
      
      // Ensure start date is before end date
      const startDateTime = new Date(startDate.year, startDate.month, startDate.day);
      const newEndDateTime = new Date(year, month, day);
      
      if (newEndDateTime < startDateTime) {
        setEndDate(startDate);
        setStartDate(newEndDate);
      } else {
        setEndDate(newEndDate);
      }
    }
  };
  
  const handleDayHover = (day, month, year) => {
    if (startDate && !endDate) {
      setHoverDate({ day, month, year });
    }
  };
  
  const handleCancel = () => {
    setStartDate(null);
    setEndDate(null);
    setHoverDate(null);
  };
  
  const handleApply = () => {
    // Here you would typically pass the selected date range to a parent component
    console.log("Applied date range:", { startDate, endDate });
  };
  
  const handleButtonClick = (buttonName) => {
    setActiveButton(buttonName);
    
    // Set predefined date ranges based on button clicked
    const today = { 
      day: new Date().getDate(), 
      month: new Date().getMonth(),
      year: new Date().getFullYear()
    };
    
    setStartDate(today);
    
    const endDate = new Date(today.year, today.month, today.day);
    
    if (buttonName === "7 Days") {
      endDate.setDate(endDate.getDate() + 7);
    } else if (buttonName === "14 Days") {
      endDate.setDate(endDate.getDate() + 14);
    } else if (buttonName === "30 Days") {
      endDate.setDate(endDate.getDate() + 30);
    } else if (buttonName === "90 Days") {
      endDate.setDate(endDate.getDate() + 90);
    } else if (buttonName === "180 Days") {
      endDate.setDate(endDate.getDate() + 180);
    } else if (buttonName === "365 Days") {
      endDate.setDate(endDate.getDate() + 365);
    } else if (buttonName === "Week") {
      // Set to this week (Sunday to Saturday)
      const day = today.day;
      const dayOfWeek = new Date(today.year, today.month, day).getDay();
      endDate.setDate(day + (6 - dayOfWeek)); // Saturday of this week
      today.day = day - dayOfWeek; // Sunday of this week
    } else if (buttonName === "Month") {
      // Set to this month (1st to last day)
      today.day = 1; // First day of month
      const lastDay = new Date(today.year, today.month + 1, 0).getDate();
      endDate.setDate(lastDay); // Last day of month
    }
    
    setEndDate({
      day: endDate.getDate(),
      month: endDate.getMonth(),
      year: endDate.getFullYear()
    });
  };
  
  return (
    <div
      className="bg-[#ffffff] box-border content-stretch flex flex-row items-start justify-start p-0 relative rounded shadow-[0px_1px_1px_0px_rgba(0,0,0,0.14),0px_2px_1px_-1px_rgba(0,0,0,0.12),0px_1px_3px_0px_rgba(0,0,0,0.2)] size-full max-h-[431px]"
      data-name="Date Picker Calendar"
    >
      <div
        className="box-border content-stretch flex flex-col gap-4 items-start justify-start p-[24px] relative shrink-0"
        data-name="month-pickers-action-bar"
      >
        <div
          className="box-border content-stretch flex flex-row gap-10 items-start justify-start p-0 relative shrink-0 overflow-x-auto"
          data-name="months-group"
        >
          <Month 
            displayMonth={displayMonths[0].month}
            displayYear={displayMonths[0].year}
            startDate={startDate}
            endDate={endDate}
            onDayClick={handleDayClick}
            hoverDate={hoverDate}
            onDayHover={handleDayHover}
            onNavigateMonth={handleMonthNavigation}
            isFirstMonth={true}
          />
          <Month 
            displayMonth={displayMonths[1].month}
            displayYear={displayMonths[1].year}
            startDate={startDate}
            endDate={endDate}
            onDayClick={handleDayClick}
            hoverDate={hoverDate}
            onDayHover={handleDayHover}
            onNavigateMonth={handleMonthNavigation}
            isFirstMonth={false}
          />
        </div>
        <ActionsBar 
          startDate={startDate ? 
            { ...startDate, month: MONTHS[startDate.month] } : null
          }
          endDate={endDate ? 
            { ...endDate, month: MONTHS[endDate.month] } : null
          }
          onApply={handleApply} 
          onCancel={handleCancel} 
        />
      </div>
      <Frame1101 activeButton={activeButton} onButtonClick={handleButtonClick} />
    </div>
  );
}

defineProperties(DatePickerCalendar, {
  allowMultipleMonths: {
    label: "Allow multiple months",
    type: "boolean",
    defaultValue: true
  },
  enableRangeSelection: {
    label: "Enable range selection",
    type: "boolean",
    defaultValue: true
  },
  selectionColor: {
    label: "Selection color",
    type: "string",
    defaultValue: "#2D64E8"
  }
});

this is the missing svg path, create a .ts file and import it:

export default {
p10001380: "M7.41 1.41L6 0L0 6L6 12L7.41 10.59L2.83 6L7.41 1.41Z",
p25284240: "M1.41 0L0 1.41L4.58 6L0 10.59L1.41 12L7.41 6L1.41 0Z",
p2d18c680: "M8 0L6.59 1.41L11.17 6L6.59 10.59L8 12L14 6L8 0Z",
p67fcb00: "M6 12L7.41 10.59L2.83 6L7.41 1.41L6 0L0 6L6 12Z",
p8039dc0: "M12.59 12L14 10.59L9.42 6L14 1.41L12.59 0L6.59 6L12.59 12Z",
}

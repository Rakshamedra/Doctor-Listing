# Doctor-Listing
import React from 'react';
import { Doctor } from '@/data/doctors';
import { Button } from '@/components/ui/button';
import { useToast } from '@/hooks/use-toast';

interface DoctorCardProps {
  doctor: Doctor;
}

const DoctorCard: React.FC<DoctorCardProps> = ({ doctor }) => {
  const { toast } = useToast();

  const handleBookAppointment = () => {
    toast({
      title: "Appointment Requested",
      description: `Your appointment with ${doctor.name} has been requested.`,
    });
  };

  return (
    <div className="bg-white rounded-lg shadow-sm p-6 mb-6">
      <div className="flex flex-col md:flex-row gap-6">
        <div className="flex-1">
          <div className="flex flex-col md:flex-row md:items-start md:justify-between">
            <div>
              <h3 className="font-bold text-lg text-gray-800">{doctor.name}</h3>
              <p className="text-gray-600">{doctor.specialty}</p>
              <p className="text-gray-500 text-sm">{doctor.qualification}</p>
              <p className="text-gray-500 text-sm">{doctor.experience} yrs exp.</p>
            </div>
           
            <div className="mt-4 md:mt-0 text-right">
              <p className="font-bold text-gray-800">₹ {doctor.fees}</p>
            </div>
          </div>
         
          <div className="mt-3 border-t pt-3">
            <div className="flex flex-col space-y-1">
              <div className="flex items-start">
                <svg className="w-5 h-5 text-gray-600 mr-2 mt-0.5" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                  <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="M19 21V5a2 2 0 00-2-2H7a2 2 0 00-2 2v16m14 0h2m-2 0h-5m-9 0H3m2 0h5M9 7h1m-1 4h1m4-4h1m-1 4h1m-5 10v-5a1 1 0 011-1h2a1 1 0 011 1v5m-4 0h4" />
                </svg>
                <span className="text-sm text-gray-600">{doctor.clinic}</span>
              </div>
              <div className="flex items-start">
                <svg className="w-5 h-5 text-gray-600 mr-2 mt-0.5" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                  <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z" />
                  <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="M15 11a3 3 0 11-6 0 3 3 0 016 0z" />
                </svg>
                <span className="text-sm text-gray-600">{doctor.location}</span>
              </div>
            </div>
          </div>
        </div>
      </div>
     
      <div className="mt-4 text-right">
        <Button
          onClick={handleBookAppointment}
          variant="outline"
          className="border-blue-600 text-blue-600 hover:bg-blue-50"
        >
          Book Appointment
        </Button>
      </div>
    </div>
  );
};

export default DoctorCard;                                                                                                               
export interface Doctor {
  id: number;
  name: string;
  specialty: string;
  qualification: string;
  specialization?: string;
  experience: number;
  clinic: string;
  location: string;
  fees: number;
  // Removed avatar property
}

export const doctors: Doctor[] = [
  {
    id: 1,
    name: "Dr. Munaf Inamdar",
    specialty: "General Physician",
    qualification: "MBBS, MD-General Medicine",
    experience: 27,
    clinic: "Apex Multispeciality and Maternity Hospital",
    location: "Kondhawa Khurd",
    fees: 600,
    // Removed avatar
  },
  {
    id: 2,
    name: "Dr. Subhash Bajaj",
    specialty: "General Physician",
    qualification: "MBBS, Diploma in Cardiology",
    experience: 11,
    clinic: "Dr. Bajaj Wellness Clinic",
    location: "Warje",
    fees: 600,
    // Removed avatar
  },
  {
    id: 3,
    name: "Dr. Mufaddal Zakir",
    specialty: "General Physician",
    qualification: "MBBS",
    experience: 27,
    clinic: "Sparsh Polyclinic",
    location: "Kondhawa",
    fees: 600,
    // Removed avatar
  },
  {
    id: 4,
    name: "Dr. Ajay Gangoli",
    specialty: "General Physician",
    qualification: "MBBS",
    experience: 34,
    clinic: "Niramaya Clinic",
    location: "Warje",
    fees: 400,
    // Removed avatar
  },
  {
    id: 5,
    name: "Dr. Devanshi Chaudhari",
    specialty: "Dentist",
    qualification: "BDS, MDS",
    experience: 8,
    clinic: "Smile Care Dental Clinic",
    location: "Aundh",
    fees: 500,
    // Removed avatar
  },
  {
    id: 6,
    name: "Dr. Devanshi Vaghani",
    specialty: "Dentist",
    qualification: "BDS",
    experience: 5,
    clinic: "City Dental Hospital",
    location: "Baner",
    fees: 450,
    // Removed avatar
  }
];

export type Specialty = "All" | "General Physician" | "Dentist" | "Neurologist" | "Oncologist" | "Ayurveda" | "Homeopath";
export type ConsultationType = "All" | "Video Consultation" | "In-clinic Consultation";
export type SortType = "Price: Low-High" | "Experience: Most Experience first";

export const specialties: Specialty[] = ["All", "General Physician", "Dentist", "Neurologist", "Oncologist", "Ayurveda", "Homeopath"];
export const consultationTypes: ConsultationType[] = ["All", "Video Consultation", "In-clinic Consultation"];
export const sortOptions: SortType[] = ["Price: Low-High", "Experience: Most Experience first"];

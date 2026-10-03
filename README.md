# test-code-.php
PHPUnit tests for authentication , recommendations ,academic perfomance and connection requests
<?php

use PHPUnit\Framework\TestCase;

require_once __DIR__ . '/../src/functions.php';

class MentorPlatformTest extends TestCase
{
    public function testValidLogin()
    {
        $result = login("student@example.com", "password123");

        $this->assertTrue($result);
    }

    public function testInvalidLogin()
    {
        $result = login("wrong@example.com", "wrongpassword");

        $this->assertFalse($result);
    }

    public function testAcademicPerformance()
    {
        $studentId = 101;

        $result = getAcademicPerformance($studentId);

        $this->assertIsArray($result);
    }

    public function testRecommendations()
    {
        $studentId = 101;

        $result = generateRecommendations($studentId);

        $this->assertIsArray($result);
    }

    public function testConnectionRequest()
    {
        $studentId = 101;
        $mentorId = 12;

        $result = sendConnectionRequest($studentId, $mentorId);

        $this->assertTrue($result);
    }

    public function testEmptyStudentIdIsRejected()
    {
        $result = getAcademicPerformance(null);

        $this->assertFalse($result);
    }
}
